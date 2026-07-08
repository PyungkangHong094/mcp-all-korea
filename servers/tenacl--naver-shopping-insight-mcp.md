# naver-shopping-insight-mcp

> **[tenacl/naver-shopping-insight-mcp](https://github.com/tenacl/naver-shopping-insight-mcp)** · ⭐ 1 · TypeScript · 최근 푸시 2025-04-07 · 카테고리: 🔎 Search & Trends

네이버 쇼핑인사이트 API로 분야별·기기별·성별·연령별 쇼핑 트렌드를 조회하는 MCP 서버입니다.

## 개요

네이버 데이터랩 쇼핑인사이트 API를 MCP 형식으로 제공하는 서버다. 특정 쇼핑 분야(카테고리)의 트렌드를 조회하고, 그 분야 내에서 기기별·성별·연령별로 세분화한 트렌드와 키워드별 트렌드를 얻을 수 있다. 주요 카테고리 ID로 패션의류(50000000), 화장품/미용(50000002), 디지털/가전(50000003), 식품(50000008) 등을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get-category-trends` | 분야별 트렌드 조회 |
| `get-category-by-device` | 분야 내 기기별 트렌드 조회 |
| `get-category-by-gender` | 분야 내 성별 트렌드 조회 |
| `get-category-by-age` | 분야 내 연령별 트렌드 조회 |
| `get-keyword-trends` | 키워드별 트렌드 조회 |

## 설치

```bash
npm install naver-shopping-insight-mcp
# 또는 소스 빌드
git clone https://github.com/tenacl/naver-shopping-insight-mcp.git
cd naver-shopping-insight-mcp && npm install && npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) (데이터랩 API) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-shopping-insight": {
      "command": "npx",
      "args": ["naver-shopping-insight-mcp"],
      "env": {
        "NAVER_CLIENT_ID": "YOUR-CLIENT-ID",
        "NAVER_CLIENT_SECRET": "YOUR-CLIENT-SECRET"
      }
    }
  }
}
```

## 비고

- 라이선스: ISC.
- 데이터 출처: [네이버 데이터랩 쇼핑 API](https://developers.naver.com/docs/datalab/shopping/).

---
*수집일: 2026-07-02 · 출처: 저장소 README*
