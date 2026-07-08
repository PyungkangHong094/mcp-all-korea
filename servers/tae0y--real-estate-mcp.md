# real-estate-mcp

> **[tae0y/real-estate-mcp](https://github.com/tae0y/real-estate-mcp)** · ⭐ 358 · Python · 최근 푸시 2026-05-10 · 카테고리: 🏠 Real Estate

Connect Claude to Korea's MOLIT real estate API and simulate buy now / buy later / invest only scenarios — 국토교통부 실거래가 기반 한국 부동산 MCP 서버.

## 개요

국토교통부(MOLIT) 공공데이터포털 Open API를 연결해 아파트·오피스텔·연립다세대·단독다가구·상업업무용 부동산의 매매·전월세 실거래가를 조회하는 MCP 서버다. 청약홈 APT 분양정보·당첨자 조회 도구도 제공하며, 소득·저축·은퇴 목표를 입력해 "지금 매수 / 나중에 매수 / 투자만" 시나리오를 금융 계산으로 시뮬레이션한다. 14개 이상의 도구를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_apartment_trades` | 아파트 매매 실거래가 조회 |
| `get_apartment_rent` | 아파트 전월세 조회 |
| `get_officetel_trades` | 오피스텔 매매 조회 |
| `get_officetel_rent` | 오피스텔 전월세 조회 |
| `get_villa_trades` | 연립다세대 매매 조회 |
| `get_villa_rent` | 연립다세대 전월세 조회 |
| `get_single_house_trades` | 단독/다가구 매매 조회 |
| `get_single_house_rent` | 단독/다가구 전월세 조회 |
| `get_commercial_trade` | 상업업무용 부동산 매매 조회 |
| `get_apt_subscription_info` | 청약홈 APT 분양정보 조회 |
| `get_apt_subscription_results` | 청약홈 신청·당첨자 정보 조회 |
| `get_region_code` | 지역(법정동) 코드 조회 |

## 설치

```bash
# uv 필요. 저장소 클론 후 stdio로 실행
git clone https://github.com/tae0y/real-estate-mcp
cd real-estate-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DATA_GO_KR_API_KEY` | [공공데이터포털](https://www.data.go.kr) (국토부 실거래가·청약홈 등 서비스별 활용신청) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "real-estate": {
      "command": "uv",
      "args": [
        "run", "--directory", "/path/to/real-estate-mcp",
        "python", "src/real_estate/mcp_server/server.py"
      ],
      "env": {
        "DATA_GO_KR_API_KEY": "your_api_key_here"
      }
    }
  }
}
```

## 비고

- stdio(로컬) 외에 HTTP(원격) 전송, Cloudflare Tunnel 리버스 프록시, Docker(`docker/docker-compose.yml`) 구성을 지원한다.
- **Deprecation Notice (2026-06-01 시행):** ChatGPT(OAuth) 지원, Caddy 리버스 프록시, 온비드(공매) 관련 도구(`get_public_auction_*`, `get_onbid_*`)가 제거될 예정이다.
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
