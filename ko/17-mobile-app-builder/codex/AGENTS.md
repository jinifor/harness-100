# Mobile App Builder Harness Codex 지침

## 목적

- 이 디렉토리는 `Mobile App Builder Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/mobile-app-builder/SKILL.md`
- 전문 agent: `.codex/agents/api-integrator.toml`, `.codex/agents/app-developer.toml`, `.codex/agents/qa-engineer.toml`, `.codex/agents/store-manager.toml`, `.codex/agents/ux-designer.toml`
- 확장 스킬: `.agents/skills/app-store-optimization/SKILL.md`, `.agents/skills/mobile-ux-patterns/SKILL.md`

## 실행 원칙

- 전체 작업은 `mobile-app-builder` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 모바일 앱의 UI/UX 설계→네이티브 코드 생성→API 연동→스토어 배포 준비를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_ux_design.md` — UX/UI 설계 문서
- `02_app_code/` — 앱 소스 코드
- `02_app_architecture.md` — 앱 아키텍처 문서
- `03_api_integration.md` — API 연동 명세
- `04_store_listing.md` — 스토어 배포 메타데이터
- `05_qa_report.md` — QA 검증 보고서
