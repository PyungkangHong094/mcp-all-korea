# vworld-mcp

> **[jeon3709-dev/vworld-mcp](https://github.com/jeon3709-dev/vworld-mcp)** · ⭐ N/A · Python · 카테고리: 🗺 Maps & Address

VWorld Open API로 필지 경계·지적정보·용도지역·공시지가를 조회하는 부동산 개발용 MCP 서버입니다.

## 개요

국토교통부 공간정보 오픈플랫폼 VWorld Open API를 감싸는 Python 로컬 MCP 서버다. 부동산 개발 타당성 검토 업무를 위해 특정 필지의 위치·경계·지적정보·용도지역지구·개별공시지가를 빠르게 조회한다. 지오코딩/역지오코딩, PNU(19자리 필지고유번호) 기반 연속지적도 조회, WFS 용도지역 공간검색, 토지특성 공시지가 조회를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `vworld_search` | 주소/장소/지번 통합 검색 (`query`, `category`: address/place) |
| `vworld_geocode` | 한글 주소 → 경위도 변환 (`address`, `address_type`: road/parcel) |
| `vworld_reverse_geocode` | 경위도 → 주소 역지오코딩 (`lat`, `lon`) |
| `vworld_get_parcel` | PNU로 연속지적도(`LP_PA_CBND_BUBUN`) 필지 경계·지번 조회 |
| `vworld_get_landuse_zone` | 용도지역지구 레이어 공간(INTERSECTS) 조회 (`pnu` 또는 `lat`/`lon`) |
| `vworld_get_individual_price` | 개별공시지가 조회(최근 3년 폴백, 원/㎡) (`pnu`) |

## 설치

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
copy .env.example .env   # VWORLD_API_KEY 입력
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `VWORLD_API_KEY` | [VWorld vworld.kr](https://www.vworld.kr) 회원가입 후 발급 | ✅ |
| `VWORLD_DOMAIN` | 배포 도메인(Cloudtype 등) | 선택 |
| `VWORLD_PROXY_URL` | 한국 IP 프록시 경유용 | 선택 |

인증키 발급 시 등록 도메인에 반드시 `localhost`를 포함해야 한다(서버가 `domain=localhost` 전송).

## 설정 예시

```json
{
  "mcpServers": {
    "vworld-mcp": {
      "command": "python",
      "args": ["c:/Users/10564/Documents/VWorld_MCP/server.py"],
      "env": {
        "VWORLD_API_KEY": "발급받은_VWORLD_API_키"
      }
    }
  }
}
```

## 비고

- 이용 정책 제약: Geocoder/Reverse Geocoder는 일 최대 30,000건, 조회 결과 저장·캐싱 금지(서버는 실시간 처리로 준수).
- VWorld는 보안(WAF) 정책상 해외 IP 요청을 네트워크 레벨에서 차단하므로, Render 등 해외 PaaS 배포 불가. 한국 IP 호스팅(Cloudtype) 권장.
- `npx @modelcontextprotocol/inspector python server.py`로 수동 검증 가능.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
