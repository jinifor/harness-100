---
name: claude-to-codex-migration
description: >-
  Convert Claude Code-oriented agent, skill, and configuration materials into the closest OpenAI Codex structure without mechanical 1:1 replacement. Trigger when: the user provides `AGENT.md`, `CLAUDE.md`, `.claude/agents/*.md`, `.claude/skills/**/skill.md`, or similar Claude-specific instructions and asks to migrate, transform, or rewrite them into Codex `AGENTS.md`, `.codex/agents/*.toml`, `.agents/skills/**/SKILL.md`, or `.codex/config.toml`. Do not trigger when: the task is only to explain Codex concepts, edit ordinary project documentation, or create a brand-new Codex agent or skill without Claude source material. Expected input: source file tree and contents, or a policy document that describes the Claude-side structure. Expected output: a migration classification summary, target tree, complete final file contents, and a `[추론한 설계]` list for any non-direct mapping.
---

# Claude Code To Codex Migration

## Goal

- Claude Code 기준 문서를 Codex가 바로 저장하고 실행할 수 있는 구조로 옮긴다.
- 파일명을 기계적으로 치환하지 말고, 각 source의 역할을 먼저 분류한 뒤 가장 가까운 Codex 개념으로 변환한다.
- 문서에 직접 대응되지 않는 판단은 숨기지 말고 `[추론한 설계]`로 명시한다.

## Source Of Truth

아래 공식 문서를 기준으로 변환한다.

- `AGENTS.md`: `https://developers.openai.com/codex/guides/agents-md`
- `Subagents`: `https://developers.openai.com/codex/subagents`
- `Skills`: `https://developers.openai.com/codex/skills`
- `Config basics`: `https://developers.openai.com/codex/config-basic`
- `Advanced config`: `https://developers.openai.com/codex/config-advanced`
- `Config reference`: `https://developers.openai.com/codex/config-reference`

공식 문서에 없는 규칙, 필드명, 경로 규칙, 동작 방식은 임의로 추가하지 않는다. 정말 필요할 때만 가장 가까운 Codex 개념으로 옮기고 `[추론한 설계]`로 표시한다.

## Core Conversion Rules

1. 의미를 유지하되 Claude 전용 표현은 Codex가 바로 이해할 수 있는 지침으로 다시 쓴다.
2. `.claude/agents/*.md`를 무조건 custom agent로 보내지 않는다.
3. Codex의 subagent는 명시적으로 spawn하는 specialist이므로, implicit 사용이 필요한 내용은 skill 또는 `AGENTS.md`를 우선한다.
4. skill의 `description`은 매우 구체적으로 작성하고 반드시 `Trigger when:`과 `Do not trigger when:`을 포함한다.
5. 입력에 없는 세부 구현을 지어내지 않는다. Codex 형식상 필수 요소를 최소한 보완할 때만 `[추론한 설계]`로 표시한다.
6. 산출물은 바로 저장 가능한 완성본으로 작성한다. 요약본, 의사코드, placeholder, `...` 생략은 금지한다.

## Classification Workflow

1. 입력 구조를 읽고 source 파일 목록을 파악한다.
2. 각 source 파일을 아래 target 중 어디로 보낼지 먼저 판정한다.
   - `AGENTS.md`
   - `AGENTS.override.md`
   - `.codex/agents/*.toml`
   - `.agents/skills/**/SKILL.md`
   - `.codex/config.toml`
3. 각 판정에 대해 한 줄 근거를 적는다.
4. 공식 문서에 직접 대응되지 않는 판단은 `note: [추론한 설계]`로 표시한다.
5. 그 다음 전체 target 디렉토리 구조를 출력한다.
6. 마지막으로 각 파일의 실제 최종 내용을 전부 출력한다.

입력이 실제 `.claude` 파일이 아니라 Claude 측 구조를 설명하는 정책 문서라면, 그 문서가 정의하는 역할을 같은 방식으로 분류한다. meta 문서를 별도 Codex artifact로 옮겨야 한다면 가장 가까운 개념을 선택하고 `[추론한 설계]`로 표시한다.

## Target Selection Guide

### `AGENTS.md`

다음에 해당하면 `AGENTS.md`로 보낸다.

- 저장소 전체 또는 특정 디렉토리에 적용되는 지속적인 작업 지침
- 프로젝트 구조, 빌드, 테스트, 린트, 코드 스타일, PR 규칙, 금지 사항, 완료 기준
- Codex가 작업 전에 읽어야 하는 standing guidance

작성 규칙:

- 명령형, 실행 가능, 구체적 문장으로 쓴다.
- Claude식 roleplay, XML 태그, 장황한 서문은 제거한다.
- 특정 하위 폴더에만 적용되는 규칙은 해당 디렉토리의 `AGENTS.md`로 분리한다.

### `AGENTS.override.md`

같은 디렉토리에서 기존 지침보다 강한 override 의미가 source에 명확할 때만 사용한다. source와 직접 대응이 약한데 override로 판단했다면 `[추론한 설계]`로 표시한다.

### `.codex/agents/*.toml`

다음에 해당하면 custom agent로 보낸다.

- 부모가 명시적으로 spawn해서 쓰는 specialist
- 역할이 좁고 분명하며 별도 담당 agent에게 맡기는 구조가 자연스러운 경우
- 필요 시 model, sandbox, MCP, skills 구성을 agent 단위로 다르게 둬야 하는 경우

필수 top-level 필드:

- `name`
- `description`
- `developer_instructions`

선택 필드:

- `model`
- `model_reasoning_effort`
- `sandbox_mode`
- `nickname_candidates`
- `[mcp_servers.*]`
- `[[skills.config]]`

작성 규칙:

- `name`은 Codex 식별 기준이므로 파일명보다 우선한다.
- 문서상 필요하지 않은 optional field는 억지로 채우지 않는다.
- `developer_instructions`에는 역할, 경계, 금지 사항, 기대 산출물을 분명히 적는다.
- `sandbox_mode`를 쓸 경우 공식 값만 사용한다.
- built-in 이름인 `default`, `worker`, `explorer`는 의도적 override가 아닌 한 사용하지 않는다.

다음은 custom agent로 보내지 않는다.

- 단순 체크리스트
- 반복 가능한 문서화 절차
- 테스트 실행 절차
- 일반적인 프로젝트 규칙

이런 내용은 skill 또는 `AGENTS.md`가 더 적합하다.

### `.agents/skills/<skill-name>/SKILL.md`

다음에 해당하면 skill로 보낸다.

- 재사용 가능한 workflow, checklist, playbook, tool-using procedure
- 일반 세션에서 직접 호출하거나 task가 description과 맞으면 implicit invocation될 수 있는 경우
- 전문가 persona보다 반복 가능한 작업 절차에 가까운 내용

필수:

- YAML front matter
- `name`
- `description`

`description` 규칙:

- 반드시 아래 형식을 포함한다.
  - `Trigger when: ...`
  - `Do not trigger when: ...`
- 가능하면 task scope, 기대 입력, 기대 출력도 포함한다.
- 한 줄짜리 모호한 요약으로 쓰지 않는다.

본문 규칙:

- 명령형, 단계별 지시문으로 작성한다.
- 입력, 절차, 출력, 검증을 분명히 적는다.
- source skill이 instruction-only라면 scripts를 지어내지 않는다.
- `scripts/`, `references/`, `assets/`, `agents/openai.yaml`은 source가 실제로 요구할 때만 추가한다.
- skill은 `.codex` 아래에 두지 않는다.

### `.codex/config.toml`

다음에 해당하면 config로 보낸다.

- 공식 문서에 대응되는 지속 설정이 있을 때만
- 전역 orchestration 또는 subagent runtime 관련 규칙이 문서화된 키로 표현 가능할 때

예시로 옮길 수 있는 키:

- `[agents].max_threads`
- `[agents].max_depth`
- `[agents].job_max_runtime_seconds`

작성 규칙:

- 공식 문서에 있는 키만 사용한다.
- 대응 키가 없는 Claude 설정은 TOML 키를 임의로 만들지 않는다.
- 필요한 경우 `AGENTS.md`나 skill의 prose 규칙으로 남기고 `[추론한 설계]`로 표시한다.

## Path Mapping Rules

- `CLAUDE.md` 또는 프로젝트 전반 규칙 문서
  - 기본적으로 루트 `AGENTS.md`
- 특정 하위 디렉토리에만 적용되는 규칙
  - 해당 디렉토리의 `AGENTS.md`
- `.claude/agents/*.md`
  - 아래 셋 중 하나로 분류
  - `.codex/agents/*.toml`
  - `.agents/skills/<skill-name>/SKILL.md`
  - `AGENTS.md` 또는 하위 디렉토리 `AGENTS.md`
- `.claude/skills/**/skill.md`
  - `.agents/skills/**/SKILL.md`
- 문서화된 전역 설정
  - `.codex/config.toml`

## Rewrite Rules

- Claude 전용 역할극 문장, XML/태그 기반 prompt 구조, Claude 고유 용어만으로 된 지시는 제거하거나 Codex 지시문으로 재작성한다.
- 문서에 없는 front matter, manifest field, 도구 권한 키, sandbox 키는 그대로 복사하지 않는다.
- standing guidance는 `AGENTS.md`로, explicit specialist는 `.codex/agents/*.toml`로, reusable workflow는 `.agents/skills/**/SKILL.md`로, documented persistent config는 `.codex/config.toml`로 옮긴다.
- source에 없는 script, asset, config key를 생성하지 않는다.

## What To Preserve

가능한 한 아래 요소를 유지한다.

- 원래의 작업 의도
- 책임 분리
- 금지 사항과 안전장치
- 빌드, 테스트, 검증 습관
- 입력과 출력 계약
- 디렉토리별 국소 규칙
- 특정 도구나 MCP 의존성

## Failure Modes To Avoid

- `.claude/agents/*.md`를 전부 custom agent로 변환하는 것
- skill `description`을 한 줄짜리 모호한 요약으로 작성하는 것
- `.codex/config.toml`에 문서 없는 키를 추가하는 것
- source에 없는 script나 asset을 생성하는 것
- 파일 내용을 요약만 하고 실제 저장 가능한 완성본을 생략하는 것
- `[추론한 설계]`가 필요한 판단을 숨기는 것

## Output Contract

반드시 아래 순서를 지켜 출력한다.

### 0) 변환 판단 요약

각 source 파일마다 아래 형식으로 정리한다.

- `source`: 원본 경로
- `target`: 변환 경로
- `kind`: `AGENTS` | `AGENTS.override` | `custom-agent` | `skill` | `config`
- `rationale`: 한 줄 설명
- `note`: 문서 직접 대응이면 비워도 되고, 추론이 들어가면 `[추론한 설계]`

### 1) 전체 디렉토리 구조

트리 형태로 출력한다.

### 2) 각 파일의 실제 내용

아래 형식을 그대로 사용한다.

--- FILE: 경로 ---
```확장자
파일 내용
```

규칙:

- 파일 내용은 완성본이어야 한다.
- placeholder 금지
- `예시` 금지
- `...` 생략 금지
- TOML, YAML, Markdown 문법이 실제로 유효해야 한다.

### 3) 추론한 설계 목록

문서에 직접 없는 매핑이나 판단만 모아서 정리한다.

- 항목
- 왜 직접 대응이 없었는지
- 왜 그 Codex 개념을 선택했는지

## Final Check

결과를 내기 전에 아래를 확인한다.

- 모든 source 파일이 정확히 하나의 target으로 분류되었는가
- skill `description`에 `Trigger when:`과 `Do not trigger when:`이 포함되었는가
- optional field를 억지로 채우지 않았는가
- `[추론한 설계]`가 필요한 판단을 명시했는가
- 산출한 파일이 실제로 저장 가능한 완성본인가
