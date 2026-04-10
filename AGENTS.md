# 저장소 지침

## 목적

- 이 저장소에서 Codex 전용 마이그레이션 자산을 관리한다.
- 프로젝트 범위의 Codex 설정은 `.codex/` 아래에 둔다.
- 재사용 가능한 Codex 워크플로는 `.agents/skills/` 아래에 둔다.

## 멀티에이전트 워크플로

- `.codex/agents/` 아래 custom agent는 사용자가 멀티에이전트 작업을 명시적으로 요청했을 때만 사용한다.
- `writer`는 역할이 같은 구현 agent다.
- `reviewer`는 역할이 같은 읽기 전용 검토 agent다.
- agent를 spawn하기 전에 부모 agent가 각 작업마다 명시적으로 파일 소유 범위를 나눠 writer들의 작업 영역이 겹치지 않게 한다.
- 각 writer와 reviewer는 같은 번호끼리 고정 쌍으로 운영한다.
- `writer`의 결과는 `reviewer`가 검증한다.
- reviewer는 짝이 되는 writer가 작업을 끝낸 뒤 같은 파일 범위를 이어받아 검토한다.
- 각 작업 묶음에서는 writer를 먼저 실행하고, 해당 writer의 reviewer를 그다음 실행한다.
- 결과를 수집한 뒤 완료된 agent thread는 닫는다.

### 역할 정의

- `writer`: 저장소 안의 Codex 관련 산출물을 작성하거나 갱신하는 동일 역할 writer
- `reviewer`: 할당된 변경 범위를 읽기 전용으로 검토하는 동일 역할 reviewer

## 변환 규칙

- 작업이 Claude-to-Codex 마이그레이션이면 `.agents/skills/claude-to-codex-migration/SKILL.md`를 워크플로 기준으로 사용한다.
- 문서화된 Codex 구조만 우선 사용한다. 문서에 없는 config key, manifest, 경로 규칙은 만들지 않는다.
- 생성한 파일은 바로 저장 가능한 완성본으로 유지한다. placeholder, 요약본, 일부만 채워진 템플릿을 남기지 않는다.
- 사용자가 명시적으로 요청하지 않은 한, 관련 없는 저장소 파일은 보존한다.

## 리뷰 규칙

- reviewer는 읽기 전용을 유지하고 findings를 먼저 보고한다.
- reviewer는 잘못된 Codex 스키마, 틀린 파일 배치, 문서에 없는 key, 필수 필드 누락, 상충하는 지침, 안전하지 않은 워크플로 지침에 집중한다.
- 이슈가 없으면 그 사실을 명시하고 남아 있는 검증 공백이 있다면 함께 적는다.
- 여러 writer를 동시에 돌릴 때는 반드시 서로 겹치지 않는 파일 범위를 배정한다.
- reviewer는 자신과 같은 번호의 writer가 맡았던 정확히 같은 범위만 검토한다.

## 검증

- `.codex/` 또는 `.agents/`를 변경한 뒤에는 바뀐 파일을 다시 읽고 필수 필드, 이름, 경로를 확인한다.
- `rg --files --hidden -g '.codex/**' -g '.agents/**' -g 'AGENTS.md'`로 기대한 트리를 확인한다.
- 이 저장소에는 이 설정 파일들을 위한 자동 build/test 스위트가 없다. 검증은 생성된 Markdown과 TOML의 구조 검토로 수행한다.
