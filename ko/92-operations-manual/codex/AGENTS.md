# Operations Manual Harness Codex 지침

## 목적

- 이 디렉토리는 `Operations Manual Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/operations-manual/SKILL.md`
- 전문 agent: `.codex/agents/document-analyst.toml`, `.codex/agents/faq-builder.toml`, `.codex/agents/flowchart-designer.toml`, `.codex/agents/manual-writer.toml`, `.codex/agents/training-producer.toml`
- 확장 스킬: `.agents/skills/flowchart-standards/SKILL.md`, `.agents/skills/knowledge-base-design/SKILL.md`

## 실행 원칙

- 전체 작업은 `operations-manual` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 업무 매뉴얼 자동 생성 하네스. 기존 문서/코드를 분석하여 프로세스 플로차트, 단계별 매뉴얼, FAQ, 교육자료를 에이전트 팀이 협업하여 생성한다.

## 산출물

- `00_input.md` — 사용자 입력 및 분석 대상 정리
- `01_document_analysis.md` — 기존 문서/코드 분석 결과
- `02_process_flowcharts.md` — 프로세스 플로차트 (Mermaid)
- `03_step_by_step_manual.md` — 단계별 업무 매뉴얼
- `04_faq_troubleshooting.md` — FAQ 및 트러블슈팅 가이드
- `05_training_materials.md` — 교육자료 패키지
- `06_review_report.md` — 통합 검증 보고서
