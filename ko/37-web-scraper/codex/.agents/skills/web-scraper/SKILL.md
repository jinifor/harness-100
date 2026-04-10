---
name: web-scraper
description: >-
  Trigger when: 사용자가 `web-scraper` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Web Scraper Harness

웹 스크래핑 시스템의 대상분석→크롤러설계→파싱→저장→모니터링을 에이전트 팀이 협업하여 구축하는 하네스.

## Specialist Agents

- `crawler-developer`: 웹 크롤러 개발자. 대상 분석 결과를 기반으로 효율적이고 안정적인 크롤러를 설계·구현한다. 요청 전략, 세션 관리, 재시도 로직, 프록시 로테이션을 담당한다.
- `data-manager`: 데이터 관리자. 파싱된 데이터의 저장, 중복 제거, 품질 검증, 내보내기를 담당한다. 스키마 설계, 인덱싱, 증분 업데이트 전략을 수립한다.
- `monitor-operator`: 모니터링 운영자. 스크래핑 시스템의 헬스체크, 사이트 변경 감지, 로깅, 알림, 스케줄링을 담당한다. 시스템의 안정적 운영을 보장한다.
- `parser-engineer`: 파싱 엔지니어. 크롤링된 원본 데이터에서 목표 데이터를 정확하게 추출하는 파싱 로직을 설계·구현한다. CSS 선택자, XPath, 정규식, JSON 파싱을 담당한다.
- `target-analyst`: 웹 스크래핑 대상 분석가. 대상 사이트의 구조 파악, robots.txt/ToS 검토, 기술 스택 분석, 안티봇 감지 메커니즘 식별, 법적 리스크 평가를 수행한다.

## Workflow

1. 사용자 요청, 제약 조건, 기존 자료를 정리한다.
2. 필요하면 `_workspace/00_input.md`에 시작 컨텍스트를 저장한다.
3. 요청 범위에 맞는 specialist를 순차 또는 병렬로 실행하고, 번호가 매겨진 `_workspace/` 산출물로 handoff 한다.
4. 리뷰어 또는 종합 검토 specialist가 있으면 마지막에 전체 결과를 검증한다.
5. 누락된 단계, 한계, 재사용한 입력 파일을 최종 보고에 명시한다.

## 작업 규칙

- source `.claude` 파일은 수정하지 않는다.
- 모든 하네스 산출물은 `_workspace/`에 유지한다.
- 기존 파일이 이미 있으면 적절한 위치에 복사하거나 참조하고 중복 단계를 건너뛸 수 있다.
- 외부 조회나 생성이 실패해도 가능한 범위까지 진행하고 한계를 적는다.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_target_analysis.md` — 대상 사이트 분석 보고서
- `02_crawler_design.md` — 크롤러 설계 및 코드
- `03_parser_logic.md` — 파싱 로직 및 코드
- `04_data_storage.md` — 데이터 저장 설계
- `05_monitor_config.md` — 모니터링 설정
- `src/` — 실제 스크래핑 소스코드

## 확장 스킬

- `.agents/skills/anti-bot-analyzer/SKILL.md`
- `.agents/skills/selector-generator/SKILL.md`
