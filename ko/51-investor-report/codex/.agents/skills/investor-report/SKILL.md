---
name: investor-report
description: >-
  Trigger when: 사용자가 `investor-report` 하네스의 전체 작업 흐름이나 주요 산출물을 한 번에 요청할 때. Do not trigger when: 확장 스킬만으로 처리할 수 있는 좁은 요청이거나, 이 하네스 범위를 벗어난 도구 실행을 요구할 때. Expected input: 사용자 요청, 제약 조건, 기존 파일, 참고 자료. Expected output: `_workspace/` 기반의 하네스 산출물과 최종 검토 결과.
---

# Investor Report Harness

투자자 보고서 생성: 재무실적분석→KPI대시보드→시장동향→전략업데이트→리스크공시를 에이전트 팀이 협업하여 생성하는 하네스.

## Specialist Agents

- `financial-analyst`: 재무 분석 전문가. P&L, 현금흐름, 주요 재무지표를 분석하고, 전기 대비·계획 대비 실적 차이를 해석하여 투자자 관점의 재무 섹션을 작성한다.
- `ir-reviewer`: IR 보고서 리뷰어(QA). 재무-KPI-시장-전략 간의 정합성을 교차 검증하고, 투자자 관점에서 보고서의 설득력·투명성·완성도를 평가한다.
- `kpi-designer`: KPI 대시보드 설계 전문가. 투자자 관점의 핵심 성과지표를 선정하고, 트렌드 시각화, 벤치마크 비교, 목표 달성률을 체계화한다.
- `market-analyst`: 시장 동향 분석 전문가. 산업 트렌드, 경쟁 환경 변화, 규제 동향, 거시경제 영향을 분석하여 투자자 보고서의 시장 섹션을 작성한다.
- `strategy-updater`: 전략 업데이트 작성 전문가. 경영 전략의 진행 상황, 향후 로드맵, 리스크 공시를 투자자 관점에서 작성한다. 최종 통합 보고서까지 완성한다.

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
- `01_financial_analysis.md` — 재무 실적 분석서
- `02_kpi_dashboard.md` — KPI 대시보드
- `03_market_trends.md` — 시장 동향 보고서
- `04_strategy_update.md` — 전략 업데이트 및 리스크 공시
- `05_review_report.md` — 리뷰 보고서
- `06_investor_report_final.md` — 최종 통합 보고서

## 확장 스킬

- `.agents/skills/financial-ratio-analyzer/SKILL.md`
- `.agents/skills/ir-narrative-builder/SKILL.md`
- `.agents/skills/kpi-benchmark-engine/SKILL.md`
