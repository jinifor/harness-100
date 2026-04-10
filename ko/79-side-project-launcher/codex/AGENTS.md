# Side Project Launcher Harness Codex 지침

## 목적

- 이 디렉토리는 `Side Project Launcher Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/side-project-launcher/SKILL.md`
- 전문 agent: `.codex/agents/idea-validator.toml`, `.codex/agents/launch-reviewer.toml`, `.codex/agents/mvp-designer.toml`, `.codex/agents/roadmap-builder.toml`, `.codex/agents/techstack-analyst.toml`
- 확장 스킬: `.agents/skills/market-sizing-calculator/SKILL.md`, `.agents/skills/techstack-decision-matrix/SKILL.md`

## 실행 원칙

- 전체 작업은 `side-project-launcher` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 사이드프로젝트 기획의 아이디어검증→기술스택선정→MVP스펙→개발로드맵→런칭체크리스트를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_idea_validation.md` — 아이디어 검증 보고서
- `02_techstack_recommendation.md` — 기술스택 추천서
- `03_mvp_spec.md` — MVP 스펙 문서
- `04_roadmap_launch.md` — 개발 로드맵 + 런칭 체크리스트
- `05_review_report.md` — 리뷰 보고서
