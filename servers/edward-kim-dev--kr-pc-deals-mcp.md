# kr-pc-deals-mcp

> **[edward-kim-dev/kr-pc-deals-mcp](https://github.com/edward-kim-dev/kr-pc-deals-mcp)** · ⭐ 10 · TypeScript · 최근 푸시 2026-03-31 · 카테고리: 🛒 Commerce & Retail

한국 PC 부품(다나와/컴퓨존) 가격비교 및 조립 견적 MCP 서버.

## 개요

다나와와 컴퓨존의 공개 웹 데이터를 수집해 PC 부품 통합 검색, 크로스사이트 최저가 비교, 가격 변동 이력(1/3/6/12개월), 조립 견적 구성, 다나와 가상견적 API 기반 CPU-메인보드-RAM 호환성 자동 검증을 제공한다. 차단 시 Zyte 프록시 자동 폴백과 지수 백오프·인메모리 캐시 등 차단 방지 메커니즘을 갖췄다. 지원 카테고리: CPU, 그래픽카드, 메인보드, RAM, SSD, HDD, 파워, 케이스, CPU 쿨러, 모니터.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_parts` | PC 부품 키워드 검색 (다나와/컴퓨존/전체) |
| `get_product_detail` | 상품 상세 정보 (스펙, 판매처별 가격) |
| `get_price_history` | 가격 변동 이력 (1/3/6/12개월) |
| `compare_prices` | 다나와↔컴퓨존 동일 제품 가격 비교 |
| `find_lowest_price` | 통합 최저가 검색 |
| `list_by_category` | 카테고리별 인기/최저가 목록 |
| `build_add` | 빌드에 부품 추가 (2개 이상 시 호환성 자동 체크) |
| `build_remove` | 빌드에서 부품 제거 |
| `build_status` | 현재 빌드 상태 조회 |
| `build_check_compatibility` | 다나와 API 기반 부품 간 호환성 체크 |
| `proxy_status` | 프록시/차단 상태 확인 |

## 설치

```bash
claude mcp add kr-pc-deals-mcp npx -- -y kr-pc-deals-mcp
```

Node.js 20 이상 필요. 소스 빌드도 지원(`npm install && npm run build`).

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `ZYTE_API_KEY` | [Zyte](https://www.zyte.com) 프록시(차단 시 자동 우회) | ❌ (미설정 시 직접 요청) |

## 설정 예시

```json
{
  "mcpServers": {
    "kr-pc-deals-mcp": {
      "command": "npx",
      "args": ["-y", "kr-pc-deals-mcp"]
    }
  }
}
```

## 비고

- 개인적·비상업적 용도 전용. 다나와/컴퓨존 이용약관 준수 책임은 사용자에게 있다(면책 조항).
- 사이트별 동시성 제어(다나와 3건/500ms, 컴퓨존 2건/1,000ms)와 3회 연속 실패 시 Zyte 프록시 전환.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
