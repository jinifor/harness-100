# Privacy Engineer Harness Codex 지침

## 목적

- 이 디렉토리는 `Privacy Engineer Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/privacy-engineer/SKILL.md`
- 전문 agent: `.codex/agents/consent-designer.toml`, `.codex/agents/pia-assessor.toml`, `.codex/agents/privacy-law-analyst.toml`, `.codex/agents/process-architect.toml`
- 확장 스킬: `.agents/skills/data-flow-mapper/SKILL.md`, `.agents/skills/gdpr-pipa-cross-reference/SKILL.md`

## 실행 원칙

- 전체 작업은 `privacy-engineer` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 개인정보보호 엔지니어링 — GDPR/PIPA 분석→PIA→동의서→프로세스설계를 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_privacy_law_analysis.md` — 법률 분석 보고서
- `02_pia_report.md` — 개인정보 영향평가 보고서
- `03_consent_documents.md` — 동의서·고지사항 세트
- `04_process_design.md` — 개인정보 처리 프로세스 설계서
