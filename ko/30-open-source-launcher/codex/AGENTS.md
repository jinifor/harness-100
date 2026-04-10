# Open Source Launcher Harness Codex 지침

## 목적

- 이 디렉토리는 `Open Source Launcher Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/open-source-launcher/SKILL.md`
- 전문 agent: `.codex/agents/code-organizer.toml`, `.codex/agents/community-manager.toml`, `.codex/agents/doc-writer.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/license-specialist.toml`
- 확장 스킬: `.agents/skills/community-health-metrics/SKILL.md`, `.agents/skills/license-compatibility-matrix/SKILL.md`

## 실행 원칙

- 전체 작업은 `open-source-launcher` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 오픈소스 프로젝트 런칭의 코드정리→문서→라이선스→커뮤니티 구축을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_code_organization.md` — 코드 정리 계획 및 결과
- `02_documentation.md` — 문서 패키지 (README, 가이드 등)
- `03_license_review.md` — 라이선스 검토 및 선정
- `04_community_setup.md` — 커뮤니티 구성 및 거버넌스
- `05_launch_report.md` — 런칭 리뷰 보고서
- `generated_files/` — 생성된 파일들 (README, LICENSE, CONTRIBUTING 등)
