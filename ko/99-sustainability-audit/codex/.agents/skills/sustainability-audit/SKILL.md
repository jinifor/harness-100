---
name: sustainability-audit
description: >-
  Trigger when: 사용자가 `sustainability-audit` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Sustainability Audit Harness

ESG/지속가능성 감사의 환경→사회→거버넌스→보고서→개선계획을 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `environmental-analyst`: ESG 환경 분석가. 탄소배출량 산정, 에너지 효율 분석, 폐기물 관리, 수자원 사용, 생물다양성 영향을 평가한다.
- `esg-reporter`: ESG 보고서 작성자. 환경·사회·거버넌스 평가 결과를 GRI, SASB, TCFD 등 국제 프레임워크에 맞춰 통합 ESG 보고서로 작성한다.
- `governance-reviewer`: ESG 거버넌스 검토자. 이사회 구조, 기업윤리, 컴플라이언스, 리스크 관리, 정보공시, 반부패 체계를 검토한다.
- `improvement-planner`: ESG 개선 계획 수립자. E/S/G 각 영역의 취약점을 분석하고, 우선순위화된 개선 로드맵, KPI, 투자 계획을 수립한다.
- `social-assessor`: ESG 사회 영향 평가자. 노동 관행, 인권, 다양성·포용성, 지역사회 기여, 공급망 사회적 책임을 평가한다.

## Workflow

1. 사용자 요청, 제약 조건, 기존 자료를 정리한다.
2. 필요하면 `_workspace/00_input.md`에 시작 컨텍스트를 저장한다.
3. 요청 범위에 맞는 specialist를 순차 또는 병렬로 실행하고, 번호가 매겨진 `_workspace/` 산출물로 handoff 한다.
4. 리뷰어 또는 종합 검토 specialist가 있으면 마지막에 전체 결과를 검증한다.
5. 누락된 단계, 한계, 재사용한 입력 파일을 최종 보고에 명시한다.

## 작업 규칙

- source `.claude` 파일은 수정하지 않는다.
- 모든 하네스 산출물은 `_workspace/`에 유지한다.
- 기존 파일이 이미 있으면 적절한 위치에 복사하거나 참조하고 중복 단계를 건너뛸 수 있다.
- 외부 조회나 생성이 실패해도 가능한 범위까지 진행하고 한계를 적는다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_environmental_assessment.md` — 환경(E) 평가서
- `02_social_assessment.md` — 사회(S) 평가서
- `03_governance_assessment.md` — 거버넌스(G) 평가서
- `04_esg_report.md` — 통합 ESG 보고서
- `05_improvement_plan.md` — 개선 계획서
- `06_review_report.md` — 교차 검증 보고서

## 확장 스킬

- `.agents/skills/ghg-protocol/SKILL.md`
- `.agents/skills/materiality-assessment/SKILL.md`
