---
name: translation-localization
description: >-
  Trigger when: 사용자가 `translation-localization` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Translation & Localization Harness

다국어 번역·현지화·문화적응·용어관리를 에이전트 팀이 협업하여 수행하는 하네스.

## Specialist Agents

- `localizer`: 현지화 전문가. 번역문을 타깃 시장의 문화적 맥락에 맞게 적응시킨다. 관용구, 비유, 도량형, 통화, 날짜/시간 형식, 문화적 민감성을 처리한다.
- `quality-reviewer`: 번역 품질 검증자(QA). 번역 정확성, 유창성, 용어 일관성, 현지화 적합성을 체계적으로 검증하고 MQM 기반 품질 점수를 산출한다.
- `style-harmonizer`: 스타일 통일자. 번역문 전체의 톤앤보이스, 문체, 격식 수준을 일관되게 유지한다. 브랜드 어조를 타깃 언어에 맞게 적용한다.
- `terminology-manager`: 용어 관리자. 번역 프로젝트의 용어집(Glossary)을 구축·유지하고, 전문 용어의 일관된 번역을 보장한다. 업계 표준 용어와 클라이언트 선호 용어를 관리한다.
- `translator`: 전문 번역가. 원문의 의미, 뉘앙스, 맥락을 정확히 분석하고 타깃 언어로 자연스럽게 옮긴다. 직역이 아닌 의역, 원문의 의도와 어조를 보존하는 번역을 수행한다.

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
- `01_source_analysis.md` — 원문 분석·번역 전략
- `02_terminology.md` — 용어집
- `03_translation.md` — 번역문
- `04_localization.md` — 현지화 적용 결과
- `05_review_report.md` — 품질 검증 보고서

## 확장 스킬

- `.agents/skills/cultural-adaptation-guide/SKILL.md`
- `.agents/skills/translation-quality-mqm/SKILL.md`
