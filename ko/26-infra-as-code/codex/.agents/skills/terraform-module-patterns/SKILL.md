---
name: terraform-module-patterns
description: >-
  Trigger when: `terraform-module-patterns` 지식이 필요한 좁은 작업이나 `infra-as-code` 하네스 내부의 하위 단계가 요청될 때. Do not trigger when: `infra-as-code` 전체 파이프라인이나 이 스킬과 무관한 작업을 수행할 때. Expected input: 작업 브리프, 초안, 문제 상황, 참고 자료. Expected output: 이 스킬 범위에 맞는 가이드, 패턴, 수정 방향.
---

재사용 가능하고 유지보수성 높은 Terraform 모듈 설계를 위한 패턴과 베스트 프랙티스.

## 디렉토리 구조 패턴

### 패턴 1: 모듈 레이어 분리

```
infrastructure/
├── modules/                    # 재사용 가능한 모듈
│   ├── networking/
│   │   ├── vpc/
│   │   │   ├── main.tf
│   │   │   ├── variables.tf
│   │   │   ├── outputs.tf
│   │   │   └── README.md
│   │   ├── security-group/
│   │   └── load-balancer/
│   ├── compute/
│   │   ├── ecs-service/
│   │   ├── lambda/
│   │   └── ec2-asg/
│   └── data/
│       ├── rds/
│       ├── elasticache/
│       └── s3/
├── environments/               # 환경별 구성
│   ├── dev/
│   │   ├── main.tf            # 모듈 호출
│   │   ├── terraform.tfvars   # 환경 변수
│   │   └── backend.tf         # 상태 저장소
│   ├── staging/
│   └── prod/
└── global/                    # 환경 공통 (IAM, DNS)
    ├── iam/
    └── route53/
```

### 패턴 2: Terragrunt 기반 DRY

```
infrastructure/
├── modules/                    # 동일
├── terragrunt.hcl             # 루트 설정 (backend, provider)
└── environments/
    ├── terragrunt.hcl         # 공통 변수
    ├── dev/
    │   ├── terragrunt.hcl     # include root + env vars
    │   ├── vpc/
    │   │   └── terragrunt.hcl # module source + inputs
    │   ├── ecs/
    │   └── rds/
    └── prod/
```

## 모듈 설계 원칙

### 1. 단일 책임 모듈

```hcl
# 좋은 예: VPC 모듈은 VPC만 담당
module "vpc" {
  source = "./modules/networking/vpc"
  cidr_block = "10.0.0.0/16"
  az_count   = 3
}

# 나쁜 예: 하나의 모듈에 모든 인프라
module "everything" {  # 안티패턴!
  source = "./modules/full-stack"
}
```

### 2. 입력/출력 설계

```hcl
# variables.tf — 유효성 검증 필수
variable "instance_type" {
  type        = string
  description = "EC2 인스턴스 타입"
  default     = "t3.medium"
  validation {
    condition     = can(regex("^t3\\.", var.instance_type))
    error_message = "t3 패밀리만 허용됩니다."
  }
}

variable "environment" {
  type = string
  validation {
    condition     = contains(["dev", "staging", "prod"], var.environment)
    error_message = "dev, staging, prod 중 하나여야 합니다."
  }
}

# outputs.tf — 다른 모듈이 필요한 값만 노출
output "vpc_id" {
  value       = aws_vpc.main.id
  description = "생성된 VPC의 ID"
}
```

### 3. 조건부 리소스

```hcl
variable "enable_monitoring" {
  type    = bool
  default = true
}

resource "aws_cloudwatch_metric_alarm" "cpu" {
  count = var.enable_monitoring ? 1 : 0
  # ...
}
```

## 상태 관리 패턴

### Remote State 구성

```hcl
# backend.tf
terraform {
  backend "s3" {
    bucket         = "company-terraform-state"
    key            = "environments/prod/vpc/terraform.tfstate"
    region         = "ap-northeast-2"
    dynamodb_table = "terraform-locks"
    encrypt        = true
  }
}
```

### 상태 분리 전략

| 전략 | 분리 기준 | 장점 | 단점 |
|------|----------|------|------|
| **환경별** | dev/staging/prod | 환경 격리, 독립 배포 | 환경 간 참조 시 data source 필요 |
| **계층별** | network/compute/data | blast radius 축소 | 참조 관계 관리 복잡 |
| **팀별** | 팀 소유 리소스 | 자율성 | 공유 리소스 관리 어려움 |
| **라이프사이클별** | 변경 빈도 | 안정 리소스 보호 | 경계 설정 어려움 |

### Cross-State 참조

```hcl
# Network 상태에서 VPC ID 읽기
data "terraform_remote_state" "network" {
  backend = "s3"
  config = {
    bucket = "company-terraform-state"
    key    = "environments/prod/network/terraform.tfstate"
    region = "ap-northeast-2"
  }
}

# 사용
resource "aws_ecs_service" "app" {
  network_configuration {
    subnets = data.terraform_remote_state.network.outputs.private_subnet_ids
  }
}
```

## 태깅 전략

```hcl
locals {
  common_tags = {
    Environment = var.environment
    Project     = var.project_name
    ManagedBy   = "terraform"
    Team        = var.team_name
    CostCenter  = var.cost_center
  }
}

resource "aws_instance" "app" {
  tags = merge(local.common_tags, {
    Name = "${var.project_name}-${var.environment}-app"
    Role = "application"
  })
}
```

## 안티패턴과 해결

| 안티패턴 | 문제 | 해결 |
|---------|------|------|
| **거대 상태 파일** | plan/apply 느림, blast radius 큼 | 계층별 분리 |
| **하드코딩 값** | 환경 간 재사용 불가 | variables + tfvars |
| **모듈 내 provider** | 유연성 상실 | provider는 루트에서만 |
| **count로 복잡한 조건** | 인덱스 변경 시 리소스 재생성 | for_each 사용 |
| **시크릿 평문 저장** | 보안 위반 | SSM/Vault 참조 |
