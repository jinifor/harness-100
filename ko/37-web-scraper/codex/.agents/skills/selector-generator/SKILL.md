---
name: selector-generator
description: >-
  Trigger when: `selector-generator` 지식이 필요한 좁은 작업이나 `web-scraper` 하네스 내부의 하위 단계가 요청될 때. Do not trigger when: `web-scraper` 전체 파이프라인이나 이 스킬과 무관한 작업을 수행할 때. Expected input: 작업 브리프, 초안, 문제 상황, 참고 자료. Expected output: 이 스킬 범위에 맞는 가이드, 패턴, 수정 방향.
---

parser-engineer의 선택자 작성 역량을 강화하는 스킬.

## 대상 에이전트

- **parser-engineer** — HTML 파싱 시 정확한 선택자 설계
- **monitor-operator** — 선택자 변경 감지 로직 구현

## 선택자 전략 우선순위

```
1순위: 고유 ID           → #product-price
2순위: data-* 속성       → [data-testid="price"]
3순위: 시맨틱 클래스      → .product-price
4순위: ARIA 속성         → [aria-label="가격"]
5순위: 구조적 선택자      → article > .info > span
6순위: 텍스트 XPath      → //span[contains(text(),"원")]
```

### 피해야 할 패턴

| 패턴 | 문제점 | 대안 |
|------|--------|------|
| `.css-1a2b3c` | CSS-in-JS 해시 변경 | 상위 시맨틱 요소 |
| `div>div>div>span` | 구조 변경 취약 | 의미 있는 클래스 |
| `:nth-child(7)` 단독 | 요소 변경 시 깨짐 | 클래스+nth 조합 |

## 선택자 패턴 레시피

### 상품 목록

```python
selectors = {
    "container": "ul.product-list > li",
    "name": ".product-name, h3.title",
    "price": {
        "current": ".sale-price, [data-price]",
        "original": ".original-price, del"
    },
    "image": "img.product-image::attr(src)",
    "link": "a.product-link::attr(href)",
    "pagination": {
        "next": "a.next, [rel='next']",
        "total": ".total-pages"
    }
}
```

### 게시판/뉴스

```python
selectors = {
    "article_list": "article, .post-item",
    "title": "h2 > a, .article-title",
    "author": ".author, .writer",
    "date": "time::attr(datetime), .date",
    "content": "article .content, .post-body"
}
```

### 테이블

```python
def table_to_dicts(html):
    headers = [th.text for th in select("thead th")]
    return [
        {h: cell.text for h, cell in zip(headers, row.select("td"))}
        for row in select("tbody tr")
    ]
```

## XPath vs CSS 판단 기준

| 상황 | 추천 | 예시 |
|------|------|------|
| ID/클래스 기반 | CSS | `#price` |
| 텍스트 포함 검색 | XPath | `//span[contains(text(),"원")]` |
| 부모 방향 탐색 | XPath | `//span[@class="price"]/parent::div` |
| 형제 관계 | XPath | `//dt[text()="가격"]/following-sibling::dd` |
| 조건부 | XPath | `//div[@class="item" and .//span[@class="sale"]]` |

## 선택자 견고성 점수 (0-100)

```
+30: ID 기반
+25: data-testid
+20: 시맨틱 클래스
+15: ARIA 속성
-10: nth-child 단독
-20: 해시 클래스
-30: 5단계+ 중첩

80-100: 안정 | 60-79: 보통 | 40-59: 취약 | 0-39: 위험
```

## 변경 감지 패턴

```python
selector_health = {
    "selector": ".product-price",
    "expected_pattern": r"[\d,]+원",
    "expected_count_min": 1,
    "fallback_selectors": ["[data-price]", "span.price"],
    "status": "active"  # active | degraded | broken
}
```

## 데이터 정제 파이프라인

```python
def clean_price(raw: str) -> int:
    return int(re.sub(r'[^\d]', '', raw))

def clean_date(raw: str) -> str:
    # 다양한 형식 → ISO 8601 변환

def clean_url(raw: str, base: str) -> str:
    return urljoin(base, raw)
```
