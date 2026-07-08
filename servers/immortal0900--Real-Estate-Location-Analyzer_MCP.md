# Real-Estate-Location-Analyzer_MCP

> **[immortal0900/Real-Estate-Location-Analyzer_MCP](https://github.com/immortal0900/Real-Estate-Location-Analyzer_MCP)** · ⭐ 0 · Python · 최근 푸시 2026-04-05 · 카테고리: 🏠 Real Estate

카카오 로컬 API로 주소 반경 내 교육·교통·편의·자연환경·미래가치 등 부동산 입지 요소를 분석하는 MCP 서버.

## 개요

카카오 로컬 API를 활용해 주소와 검색 반경을 입력하면 교육환경(학교·학원), 교통여건(지하철·버스), 편의여건(마트·병원), 자연환경(공원), 미래가치(재건축) 등 입지 핵심 요소의 명칭·주소·거리를 반환한다. MCP 서버와 Gradio 웹 앱을 함께 제공하며 Hugging Face Spaces에서 원격 MCP 엔드포인트로도 연결 가능. (Huggingface MCP 1st Birthday 해커톤 출품작.) Python, FastMCP + Gradio.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `analyze_location` | 주소의 종합 입지 분석 — `address`, `radius`(m, 기본 3000) |
| `get_address_coordinates` | 주소 → 위도/경도 좌표 변환 — `address` |

## 설치

```bash
# 로컬 MCP 서버
uv venv && source .venv/bin/activate
uv pip install -r requirements.txt
cp .env.example .env   # KAKAO_REST_API_KEY 입력
python src/mcp_server.py
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KAKAO_REST_API_KEY` | [카카오 Developers](https://developers.kakao.com) | ✅ |

## 설정 예시

로컬 실행:

```json
{
  "mcpServers": {
    "real-estate-location": {
      "command": "python",
      "args": ["C:/real_estate_location_mcp/src/mcp_server.py"],
      "env": { "KAKAO_REST_API_KEY": "your_kakao_api_key_here" }
    }
  }
}
```

원격 HF Space 엔드포인트(설치 불필요):

```json
{
  "mcpServers": {
    "real-estate-analyzer": {
      "url": "https://immortal0900-real-estate-location-analyzer-mcp.hf.space/gradio_api/mcp/sse"
    }
  }
}
```

## 비고

- 라이선스: MIT. Gradio SDK 기반 Hugging Face Space로도 배포됨.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
