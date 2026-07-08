# naver-land-mcp

> **[Seonh0/naver-land-mcp](https://github.com/Seonh0/naver-land-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-04-17 · 카테고리: 🏠 Real Estate

네이버 부동산 비공식 API로 전국 아파트 매물·시세·실거래가를 조회하는 6개 도구 MCP 서버.

## 개요

네이버 부동산의 비공식 내부 API를 사용해 동/구/군 + 가격 범위로 아파트 매물(매매/전세/월세)을 검색하고, 관심 단지의 매물·시세·실거래가를 스냅샷 비교로 변동 감지하며, 단지 상세와 평형별 시세를 조회한다. 요청 간 최소 0.5초 딜레이로 IP 차단을 방어. Python, FastMCP(`server.py`) + 클라이언트/필터/리포트/스냅샷 모듈 구성.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_apartments` | 동/구/군 + 가격 범위로 매물 검색 (매매/전세/월세) |
| `watch_complexes` | 관심 단지 매물+시세+실거래가 조회, 이전 스냅샷 대비 변동 감지 |
| `get_complex_info` | 단지 상세 (세대수, 준공일, 평형, 좌표 등) |
| `get_complex_price_info` | 단지 평형별 시세(네이버) + 최근 실거래가 |
| `resolve_district` | 지역명 → 네이버 cortarNo 조회 |
| `list_districts` | 전국 시/도 17개 목록 |

## 설치

```bash
git clone <repo-url> && cd naver-land-mcp
# 의존성은 uv run 이 자동 설치 (별도 설치 단계 없음)
```

## 필요 키 · 환경변수

API 키 불필요 (네이버 부동산 비공식 API 직접 호출).

## 설정 예시

```json
{
  "mcpServers": {
    "naver-land": {
      "command": "uv",
      "args": ["run", "--directory", "/ABSOLUTE/PATH/TO/naver-land-mcp", "server.py"]
    }
  }
}
```

## 비고

- 라이선스: MIT. 비공식 내부 API 사용 — 응답 구조·차단 정책이 사전 통보 없이 바뀔 수 있으며, 저장소 자체가 예고 없이 비공개/삭제될 수 있다고 README가 명시.
- 요청 간 최소 0.5초 딜레이(`config.REQUEST_DELAY_SEC`) — 상업적 이용 비권장, 개인 학습·조회 용도.
- `docs/`에 API 레퍼런스·도구 스펙·모듈 가이드·테스트·배포 문서 포함.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
