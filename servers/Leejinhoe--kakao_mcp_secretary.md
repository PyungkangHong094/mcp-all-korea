# kakao_mcp_secretary

> **[Leejinhoe/kakao_mcp_secretary](https://github.com/Leejinhoe/kakao_mcp_secretary)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🗺 Maps & Address

카카오 로컬·모빌리티·톡캘린더·메시지 API로 일정 중복과 이동 불가 동선을 감지하고 경로를 최적화하는 생활동선 보조 MCP 서버입니다.

## 개요

"DailyRoute Guard(생활동선 캘린더 가드)"라는 이름의 MCP 서버로, 텍스트나 OCR 텍스트에서 일정을 추출해 로컬 SQLite DB에 저장하고, 일정 중복·이동 불가능한 동선을 미리 감지한다. 카카오 로컬·모빌리티·톡캘린더·메시지 API를 활용하며, API 키가 없어도 mock/fallback 모드로 데모가 가능하다. Streamable HTTP(`/mcp`) 방식으로 동작하고 PlayMCP 배포를 염두에 둔 Docker/GHCR 가이드를 포함한다.

## 제공 도구

README의 "MCP Tool 목록"에 명시된 도구:

| 도구 | 기능 |
|------|------|
| `health_check` | 서버 상태 확인 |
| `extract_schedule_from_text` | 텍스트/OCR 텍스트에서 일정 추출 |
| `save_schedule` | 일정 저장, 중복 경고, 자동 이동 가능성 확인 |
| `list_schedules` | 워크스페이스별 일정 조회 |
| `update_schedule` | 일정 수정 및 이동 가능성 재확인 |
| `delete_schedule` | 일정 삭제 |
| `check_conflict` | 저장 전 일정 충돌 확인 |
| `check_day_feasibility` | 하루 일정의 이동 가능성 확인 |
| `find_places_on_route` | 동선 중 심부름 경유지 추천 |
| `manage_route_preferences` | 동선 프로필·심부름·생활 루틴 저장/조회 |
| `connect_kakao_calendar` | 카카오 캘린더 연결 상태·로그인 URL 확인 |
| `sync_to_talk_calendar` | 저장된 일정을 톡캘린더에 동기화 |
| `build_daily_route_briefing` | 일일 동선 브리핑 생성 |
| `create_route_watch` | 일정 전 경로 감시 등록 |
| `get_route_alerts` | 최근 경로 경고 조회 |

## 설치

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python server.py
```

로컬 MCP 엔드포인트는 `http://127.0.0.1:8000/mcp`(Streamable HTTP), health check는 `http://127.0.0.1:8000/health`. SQLite DB는 기본적으로 `data/dailyroute_guard.db`에 생성된다. Docker/GHCR 배포도 지원한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KAKAO_REST_API_KEY` | [카카오 개발자센터](https://developers.kakao.com) | ⬜ |
| `KAKAO_MOBILITY_API_KEY` | 카카오 모빌리티 | ⬜ |
| `ENABLE_REAL_KAKAO_APIS` | 실 API 사용 토글 | ⬜ |
| `KAKAO_OAUTH_SCOPES` | `talk_message,talk_calendar` 등 | ⬜ |

키가 없어도 서버는 동작하며 mock/fallback 결과를 한국어로 표시한다. 실제 카카오 API를 쓰려면 위 키를 `secrets.local.json` 등으로 주입하고 OAuth Redirect URI를 카카오 Developers에 등록해야 한다.

## 설정 예시

```json
{
  "mcpServers": {
    "dailyroute-guard": {
      "url": "http://127.0.0.1:8000/mcp"
    }
  }
}
```
*(README 기반 구성 — README는 로컬 실행/PlayMCP 배포 위주로 기술되어 있음)*

## 비고

- 초기 메신저 대화방 자동 읽기·답장 아이디어는 공식 API 제약으로 제외하고, 공식 API+로컬 DB만으로 가능한 일정/동선 문제로 피벗했다(README 명시).
- 공모전(PlayMCP in KC) 배포를 전제로 한 프로젝트로, 서버 이름 제한 단어·Dockerfile·PAT 관련 배포 주의사항이 README에 상세히 안내되어 있다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
