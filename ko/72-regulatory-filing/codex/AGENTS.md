# Regulatory Filing Harness Codex 지침

## 목적

- 이 디렉토리는 `Regulatory Filing Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/regulatory-filing/SKILL.md`
- 전문 agent: `.codex/agents/attachment-preparer.toml`, `.codex/agents/document-drafter.toml`, `.codex/agents/requirements-investigator.toml`, `.codex/agents/submission-verifier.toml`
- 확장 스킬: `.agents/skills/form-filling-guide/SKILL.md`, `.agents/skills/permit-requirements-db/SKILL.md`

## 실행 원칙

- 전체 작업은 `regulatory-filing` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 인허가·신고서류의 요건조사→구비서류목록→신청서작성→첨부자료준비→제출체크리스트를 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_requirements_research.md` — 요건 조사 보고서
- `02_document_list.md` — 구비서류 목록
- `03_application_draft.md` — 신청서 초안
- `04_attachments_guide.md` — 첨부자료 준비 가이드
- `05_submission_checklist.md` — 제출 체크리스트 및 검증 보고서
