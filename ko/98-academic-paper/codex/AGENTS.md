# Academic Paper Harness Codex 지침

## 목적

- 이 디렉토리는 `Academic Paper Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/academic-paper/SKILL.md`
- 전문 agent: `.codex/agents/experiment-manager.toml`, `.codex/agents/paper-writer.toml`, `.codex/agents/research-designer.toml`, `.codex/agents/statistical-analyst.toml`, `.codex/agents/submission-preparer.toml`
- 확장 스킬: `.agents/skills/citation-standards/SKILL.md`, `.agents/skills/research-methodology/SKILL.md`

## 실행 원칙

- 전체 작업은 `academic-paper` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 학술 논문 작성의 연구설계→실험→분석→집필→투고준비를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_research_design.md` — 연구 설계서
- `02_experiment_protocol.md` — 실험 프로토콜
- `03_analysis_report.md` — 분석 보고서
- `04_manuscript.md` — 논문 원고
- `05_submission_package.md` — 투고 패키지
- `06_review_report.md` — 통합 리뷰 보고서
