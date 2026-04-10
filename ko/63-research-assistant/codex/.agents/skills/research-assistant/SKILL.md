---
name: research-assistant
description: >-
  Trigger when: 사용자가 `research-assistant` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Research Assistant Harness

학술 연구 보조 에이전트 팀 하네스.

## Specialist Agents

- `critic-synthesizer`: 비평·종합 전문가. 수집된 문헌을 비판적으로 분석하고, 연구 갭을 식별하며, 주제별 종합을 통해 문헌 리뷰의 핵심 내러티브를 구성한다.
- `literature-searcher`: 문헌 검색 전문가. 학술 데이터베이스와 웹을 탐색하여 연구 주제에 관련된 논문·서적·보고서를 체계적으로 수집하고 관련성을 평가한다.
- `note-taker`: 메모 작성 전문가. 각 문헌을 정독하여 핵심 논지, 방법론, 주요 발견, 인용 가치 있는 구절을 구조화된 형태로 정리한다.
- `reference-manager`: 참고문헌 관리 전문가. 모든 인용 문헌의 서지 정보를 정확하게 관리하고, 요청된 인용 형식(APA, MLA, Chicago 등)으로 변환하며, 중복·누락을 검증한다.
- `research-coordinator`: 연구 조율자(QA). 문헌 검색·메모·비평·참고문헌 간의 일관성을 교차 검증하고, 연구 품질 기준 충족 여부를 확인하여 최종 보고서를 작성한다.

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

## 확장 스킬

- `.agents/skills/citation-formatter/SKILL.md`
- `.agents/skills/systematic-review-protocol/SKILL.md`
