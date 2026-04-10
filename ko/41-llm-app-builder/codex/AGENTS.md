# LLM App Builder Harness Codex 지침

## 목적

- 이 디렉토리는 `LLM App Builder Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/llm-app-builder/SKILL.md`
- 전문 agent: `.codex/agents/deploy-engineer.toml`, `.codex/agents/eval-specialist.toml`, `.codex/agents/optimization-engineer.toml`, `.codex/agents/prompt-engineer.toml`, `.codex/agents/rag-architect.toml`
- 확장 스킬: `.agents/skills/chunking-strategy-guide/SKILL.md`, `.agents/skills/prompt-optimizer/SKILL.md`

## 실행 원칙

- 전체 작업은 `llm-app-builder` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- LLM 앱 개발의 프롬프트엔지니어링→RAG파이프라인설계→평가프레임워크→최적화→배포설정을 에이전트 팀이 협업하여 수행하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_prompt_design.md` — 프롬프트 설계서
- `02_rag_pipeline.md` — RAG 파이프라인 설계
- `03_eval_framework.md` — 평가 프레임워크
- `04_optimization.md` — 최적화 전략
- `05_deploy_config.md` — 배포 설정
- `src/` — 앱 소스코드
