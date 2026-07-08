# cairn

> **[heznpc/cairn](https://github.com/heznpc/cairn)** · ⭐ 0 · TypeScript · 최근 푸시 2026-07-07 · 카테고리: 🗺 Maps & Address

주소를 입력하면 한국식 약도(pictogram map) SVG를 자동 생성하는 MCP 서버 + CLI.

## 개요

주소를 입력하면 한국식 약도(略地図)를 SVG로 자동 생성하는 MCP 서버다. OpenStreetMap의 Nominatim(지오코딩)과 Overpass(POI·도로) API만 사용해 API 키 없이 동작한다. 랜드마크를 결정론적 휴리스틱으로 큐레이션(교통 > 공공 > 상점 가중치, ~150m 스윗스팟, 카테고리 다양성)하고, 도로를 중요도 등급으로 분류·단순화(Douglas-Peucker)해 픽토그램 SVG로 렌더링한다. 서버는 에이전트가 아닌 순수 도구를 지향해 서버 측 LLM 호출이 없다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `generate_map` | 주소 → 약도 SVG 원샷 생성 |
| `geocode` | 주소 → 좌표 변환 (Nominatim) |
| `find_landmarks` | 좌표 → 주변 POI 목록 (Overpass) |
| `find_roads` | 좌표 → 단순화된 도로 폴리라인 (Overpass) |

## 설치

```bash
# npm 패키지: @yakdo/cairn (stdio MCP 서버 + CLI)
npx -y @yakdo/cairn
```
(README 기반 구성 — README는 CLI 예시 `node dist/cli.js` 위주)

## 필요 키 · 환경변수

API 키 불필요 — OSM Nominatim + Overpass만 사용(계정·쿼터 가입 불요).

## 설정 예시

```json
{
  "mcpServers": {
    "cairn": {
      "command": "npx",
      "args": ["-y", "@yakdo/cairn"]
    }
  }
}
```
(README 기반 구성)

## 비고

- 검색 반경 최대 5km, SVG 캔버스 최대 4000px로 제한. Nominatim 1.1s / Overpass 1req/s 요청 간격을 지켜 공개 OSM 서비스를 보호한다.
- 레이아웃 모드(`diagram`/`geographic`), 출력 프리셋(`standard`/`compact`/`minimal`/`schematic`/`badge`), 목적지 포커스(`--focus`) 등 CLI 옵션 다양. 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
