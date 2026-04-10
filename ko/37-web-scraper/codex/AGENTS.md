# Web Scraper Harness Codex 지침

## 목적

- 이 디렉토리는 `Web Scraper Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/web-scraper/SKILL.md`
- 전문 agent: `.codex/agents/crawler-developer.toml`, `.codex/agents/data-manager.toml`, `.codex/agents/monitor-operator.toml`, `.codex/agents/parser-engineer.toml`, `.codex/agents/target-analyst.toml`
- 확장 스킬: `.agents/skills/anti-bot-analyzer/SKILL.md`, `.agents/skills/selector-generator/SKILL.md`

## 실행 원칙

- 전체 작업은 `web-scraper` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 웹 스크래핑 시스템의 대상분석→크롤러설계→파싱→저장→모니터링을 에이전트 팀이 협업하여 구축하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_target_analysis.md` — 대상 사이트 분석 보고서
- `02_crawler_design.md` — 크롤러 설계 및 코드
- `03_parser_logic.md` — 파싱 로직 및 코드
- `04_data_storage.md` — 데이터 저장 설계
- `05_monitor_config.md` — 모니터링 설정
- `src/` — 실제 스크래핑 소스코드
