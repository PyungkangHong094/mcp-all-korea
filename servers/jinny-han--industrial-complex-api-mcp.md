# industrial-complex-api-mcp

> **[jinny-han/industrial-complex-api-mcp](https://github.com/jinny-han/industrial-complex-api-mcp)** · ⭐ - · Python · 카테고리: 📊 Public Data

전국 1,428개 산업단지(국가·일반·도시첨단·농공) 정보를 자연어로 검색·조회하는 MCP 서버.

## 개요

KICOX 전국산업단지현황통계(XLSX)와 국토교통부 경계·점형 도면(SHP)을 결합해 1,428개 산업단지의 위치·면적·분양률·입주/가동업체수를 즉시 조회한다. SHP-KICOX 매칭 정확도 98.9%(수동·exact·substring·fuzzy 단계). KICOX OpenAPI 키를 등록하면 분기별 가동·생산·수출·고용 통계까지 확장된다. 정적 데이터는 `scripts/bootstrap.py`가 로그인·키 없이 자동 다운로드한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_complexes` | 단지명·시도·시군·유형·태그 검색(fuzzy 매칭) |
| `get_complex` | DAN_ID 또는 이름으로 단지 상세(좌표·면적·통계) |
| `get_complex_stats` | KICOX OpenAPI 동적 통계(가동률·생산·수출·고용 등 12종) |
| `get_server_info` | 서버 상태·데이터 분포 진단 |

## 설치

```bash
git clone https://github.com/heeseokuyang/industrial-complex-api-mcp
cd industrial-complex-api-mcp
python -m venv .venv && .venv\Scripts\activate
pip install -r requirements.txt
python scripts/bootstrap.py           # 공개 데이터 자동 다운로드(5MB)
python -m industrial_complex_mcp.server
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KICOX_API_KEY` | [공공데이터포털 15152884](https://www.data.go.kr/data/15152884/openapi.do) | ⛔(동적 통계 시만) |

키 없이도 정적 데이터(1,428개 단지 정보)는 정상 동작.

## 설정 예시

```json
{
  "mcpServers": {
    "industrial-complex-kr": {
      "command": "python",
      "args": ["-m", "industrial_complex_mcp.server"],
      "cwd": "C:/path/to/industrial-complex-api-mcp",
      "env": { "PYTHONPATH": "C:/path/to/industrial-complex-api-mcp/src", "KICOX_API_KEY": "YOUR_KEY_OR_OMIT" }
    }
  }
}
```

## 비고

- 읍면동·상세주소 없음(시군까지). 지오코딩은 별도 필요.
- MVP 단계 — search ranking·error handling 개선 여지.
- 데이터 라이선스: 공공누리 제4유형.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
