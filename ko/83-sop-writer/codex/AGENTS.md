# SOP Writer Harness Codex 지침

## 목적

- 이 디렉토리는 `SOP Writer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/sop-writer/SKILL.md`
- 전문 agent: `.codex/agents/checklist-designer.toml`, `.codex/agents/procedure-writer.toml`, `.codex/agents/process-analyst.toml`, `.codex/agents/training-developer.toml`, `.codex/agents/version-controller.toml`
- 확장 스킬: `.agents/skills/checklist-design/SKILL.md`, `.agents/skills/process-mapping/SKILL.md`

## 실행 원칙

- 전체 작업은 `sop-writer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 표준운영절차(SOP)의 프로세스분석→절차서→체크리스트→교육자료→버전관리를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_process_analysis.md` — 프로세스 분석 결과
- `02_procedure_document.md` — 표준 절차서
- `03_checklists.md` — 체크리스트 세트
- `04_training_materials.md` — 교육자료
- `05_version_control.md` — 버전 관리 및 검증 보고서
