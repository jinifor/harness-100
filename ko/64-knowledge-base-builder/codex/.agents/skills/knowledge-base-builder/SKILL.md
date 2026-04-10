---
name: knowledge-base-builder
description: >-
  Trigger when: 사용자가 `knowledge-base-builder` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Knowledge Base Builder Harness

조직 지식관리 체계 구축 에이전트 팀 하네스.

## Specialist Agents

- `knowledge-collector`: 지식 수집가. 조직 내 문서, 코드베이스, 프로세스, 암묵지 등 다양한 소스에서 지식을 체계적으로 추출하고 인벤토리를 구성한다.
- `maintenance-planner`: 유지보수 플래너. 지식 베이스의 장기적 품질을 보장하기 위한 거버넌스 모델, 갱신 주기, 품질 관리 프로세스, 기여 가이드라인을 수립한다.
- `search-optimizer`: 검색 최적화 전문가. 위키 콘텐츠의 검색 가능성을 극대화하기 위한 메타데이터, 키워드 전략, 검색 인덱스를 설계한다.
- `taxonomy-designer`: 분류 체계 설계자. 수집된 지식을 논리적 카테고리로 분류하고, 태그 체계·계층 구조·네비게이션 경로를 설계한다.
- `wiki-builder`: 위키 빌더. 분류 체계를 기반으로 실제 마크다운 위키 페이지를 생성하고, 페이지 간 상호 링크·목차·템플릿을 구성한다.

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

- `.agents/skills/content-lifecycle-manager/SKILL.md`
- `.agents/skills/information-architecture/SKILL.md`
