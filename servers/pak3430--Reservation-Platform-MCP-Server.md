# Reservation-Platform-MCP-Server

> **[pak3430/Reservation-Platform-MCP-Server](https://github.com/pak3430/Reservation-Platform-MCP-Server)** · ⭐ N/A · Python · 카테고리: 🛒 Commerce & Retail

네이버·에어비앤비·스페이스클라우드·야놀자·카카오 예약을 iCal 표준으로 통합 관리하는 MCP 서버입니다.

## 개요

여러 예약 플랫폼(네이버 예약, 에어비앤비, 스페이스클라우드, 야놀자, 카카오 예약)의 실제 예약 데이터를 iCal 표준(각 플랫폼이 제공하는 iCal URL)으로 한 곳에서 통합 관리하는 Python FastMCP 서버다. 서버 시작 시 전 플랫폼 예약을 자동 동기화하고 1시간마다 재동기화한다. 예약 조회·중복 방지·매출 정산·고객 관리·안내 메시지 생성 기능을 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_today_reservations` | 오늘 예약 현황 조회 |
| `get_reservations_by_date` | 특정 날짜 예약 조회 |
| `get_reservations_by_platform` | 플랫폼별 예약 조회 |
| `get_week_reservations` | 이번 주 예약 조회 |
| `check_duplicate_reservations` | 중복 예약 감지 |
| `check_time_slot` | 특정 시간대 예약 가능 여부 확인 |
| `get_revenue_summary` | 매출 요약(일/주/월) |
| `calculate_platform_fees` | 플랫폼 수수료 계산 |
| `get_blacklist` | 블랙리스트 조회 |
| `add_to_blacklist` | 블랙리스트 추가 |
| `get_noshow_customers` | 노쇼 고객 조회 |
| `generate_reminder_message` | 예약 안내 메시지 생성 |
| `sync_platform_ical` | 실시간 iCal URL에서 예약 동기화 |

## 설치

```bash
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

실행(STDIO): `python3 -m src.server`
실행(HTTP): `TRANSPORT=http PORT=8000 python3 -m src.server`

## 필요 키 · 환경변수

외부 API 키는 없으나, 각 플랫폼의 iCal URL을 환경변수(`.env`)로 설정해야 실데이터가 연동된다.

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `AIRBNB_ICAL_URL` | 에어비앤비 호스팅 → 캘린더 내보내기 | 선택 |
| `NAVER_ICAL_URL` | 네이버 예약 관리 → 캘린더 설정 → iCal 내보내기 | 선택 |
| `SPACECLOUD_ICAL_URL` | 스페이스클라우드 캘린더 | 선택 |
| `TRANSPORT` / `PORT` | HTTP 모드 실행 설정 | 선택 |

## 설정 예시

```json
{
  "mcpServers": {
    "reservation-platform": {
      "command": "python",
      "args": ["-m", "src.server"],
      "cwd": "/path/to/PlayMCP",
      "env": {
        "PATH": "/path/to/PlayMCP/venv/bin:${PATH}"
      }
    }
  }
}
```

## 비고

- Python 3.12+, FastMCP, iCalendar(ics) 파싱 기반. 프로젝트 코드명은 `PlayMCP`.
- 실제 iCal URL 없이도 `test_data.py`로 샘플 데이터를 생성해 테스트할 수 있다.
- iCal URL 획득 방법은 저장소의 `ICAL_SETUP_GUIDE.md` 참고.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
