# Documentary Research Harness Codex 지침

## 목적

- 이 디렉토리는 `Documentary Research Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/documentary-research/SKILL.md`
- 전문 agent: `.codex/agents/fact-checker.toml`, `.codex/agents/interviewer.toml`, `.codex/agents/narrator.toml`, `.codex/agents/researcher.toml`, `.codex/agents/story-architect.toml`
- 확장 스킬: `.agents/skills/interview-design/SKILL.md`, `.agents/skills/investigative-research/SKILL.md`, `.agents/skills/narrative-structure/SKILL.md`

## 실행 원칙

- 전체 작업은 `documentary-research` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 다큐멘터리 리서치·구성안·인터뷰질문·내레이션 대본을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_research_brief.md` — 리서치 브리프
- `02_structure.md` — 구성안/구조 설계
- `03_interview_guide.md` — 인터뷰 가이드
- `04_narration_script.md` — 내레이션 대본
- `05_review_report.md` — 팩트체크/리뷰 보고서
