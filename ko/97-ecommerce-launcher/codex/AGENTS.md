# E-commerce Launcher Harness Codex 지침

## 목적

- 이 디렉토리는 `E-commerce Launcher Harness` Claude 하네스를 Codex 구조로 옮긴 결과물이다.
- 지속 지침은 이 파일에 두고, 역할 분리는 `.codex/agents/`에 둔다.
- 반복 가능한 워크플로는 `.agents/skills/`에 둔다.

## 구조

- 오케스트레이션 스킬: `.agents/skills/ecommerce-launcher/SKILL.md`
- 전문 agent: `.codex/agents/cs-architect.toml`, `.codex/agents/detail-page-writer.toml`, `.codex/agents/marketing-manager.toml`, `.codex/agents/pricing-strategist.toml`, `.codex/agents/product-planner.toml`
- 확장 스킬: `.agents/skills/conversion-optimization/SKILL.md`, `.agents/skills/product-copy-formulas/SKILL.md`

## 실행 원칙

- 전체 작업은 `ecommerce-launcher` skill로 시작한다.
- 명시적 위임이 필요할 때만 `.codex/agents/*.toml`을 specialist로 사용한다.
- 모든 산출물은 `_workspace/`에 저장한다.
- 리뷰어 또는 종합 검토 역할이 있으면 findings를 먼저 제시한다.
- source `.claude` 파일은 수정하지 않는다.
- 문서에 없는 Codex key, manifest, extra script/asset은 만들지 않는다.

## 개요

- 이커머스 상품 런칭의 기획→상세페이지→가격전략→마케팅→CS 셋업을 에이전트 팀이 협업하여 생성하는 하네스.

## 산출물

- `00_input.md` — 사용자 입력 정리
- `01_product_brief.md` — 상품 기획서
- `02_detail_page.md` — 상세페이지 원고
- `03_pricing_plan.md` — 가격 전략서
- `04_marketing_plan.md` — 마케팅 플랜
- `05_cs_manual.md` — CS 운영 매뉴얼
- `06_review_report.md` — 통합 리뷰 보고서
