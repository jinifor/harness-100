---
name: llm-app-builder
description: >-
  Trigger when: 사용자가 `llm-app-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# LLM App Builder Harness

LLM 앱 개발의 프롬프트엔지니어링→RAG파이프라인설계→평가프레임워크→최적화→배포설정을 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `deploy-engineer`: LLM 앱 배포 엔지니어. API 서버, 스케일링, 모니터링, 가드레일 런타임을 포함한 프로덕션 배포를 설정한다.
- `eval-specialist`: LLM 평가 전문가. 프롬프트 품질, RAG 검색 성능, 전체 앱 품질을 평가하는 프레임워크를 설계한다. 벤치마크, A/B 테스트, 회귀 테스트를 구축한다.
- `optimization-engineer`: LLM 앱 최적화 엔지니어. 비용, 레이턴시, 품질의 트레이드오프를 최적화한다. 프롬프트 압축, 캐싱, 모델 라우팅, 배치 처리를 담당한다.
- `prompt-engineer`: 프롬프트 엔지니어. LLM 앱의 시스템 프롬프트, few-shot 예시, 출력 포맷, 가드레일을 설계한다. 프롬프트의 안정성과 품질을 보장한다.
- `rag-architect`: RAG 파이프라인 설계자. 문서 처리, 청킹, 임베딩, 벡터 저장소, 검색, 리랭킹을 포함한 전체 RAG 파이프라인을 설계·구현한다.

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
- `01_prompt_design.md` — 프롬프트 설계서
- `02_rag_pipeline.md` — RAG 파이프라인 설계
- `03_eval_framework.md` — 평가 프레임워크
- `04_optimization.md` — 최적화 전략
- `05_deploy_config.md` — 배포 설정
- `src/` — 앱 소스코드

## 확장 스킬

- `.agents/skills/chunking-strategy-guide/SKILL.md`
- `.agents/skills/prompt-optimizer/SKILL.md`
