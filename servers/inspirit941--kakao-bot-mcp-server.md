# kakao-bot-mcp-server

> **[inspirit941/kakao-bot-mcp-server](https://github.com/inspirit941/kakao-bot-mcp-server)** · ⭐ (조회 실패) · Python · 최근 푸시 (조회 실패) · 카테고리: 🤝 Collaboration & Communication

카카오 Developers API(카카오톡 메시지 전송·톡캘린더)를 AI 에이전트에 통합하는 MCP 서버입니다.

## 개요

카카오 Developers API를 AI 에이전트에 통합하는 MCP 서버 구현 예시다. 카카오톡 메시지 API('나에게 보내기' 기본 템플릿)로 텍스트·피드·리스트·위치·캘린더·커머스 메시지를 자신에게 전송하고, 톡캘린더 API로 캘린더 목록 조회와 서브 캘린더 생성/수정/삭제를 수행한다. OAuth2 토큰은 프로젝트 루트의 `.oauth2.<이메일>.json` 파일로 관리된다.

## 제공 도구

README의 Tools 섹션에 명시된 도구. 모든 도구는 사용자 자격 식별용 `__email_address__` 입력을 요구한다.

**카카오톡 메시지 API ('나에게 보내기')**

| 도구 | 기능 |
|------|------|
| `send_text_template_to_me` | 텍스트 메시지 전송 |
| `send_feed_template_to_me` | 피드 메시지 전송 |
| `send_list_template_to_me` | 리스트 메시지 전송 |
| `send_location_template_to_me` | 위치 메시지 전송 |
| `send_calendar_template_to_me` | 캘린더 메시지 전송 |
| `send_commerce_template_to_me` | 커머스 메시지 전송 |

**톡캘린더 API**

| 도구 | 기능 |
|------|------|
| `get_calendar_list` | 사용자 캘린더 목록 조회 |
| `create_sub_calendar` | 서브 캘린더 생성 |
| `update_sub_calendar` | 서브 캘린더 수정 |
| `delete_sub_calendar` | 서브 캘린더 삭제 |

## 설치

```bash
git clone git@github.com:inspirit941/kakao-bot-mcp-server.git
cd kakao-bot-mcp-server
pip install uv
uv sync
uv run mcp-kakao
```

Python 3.13+, uv 필요. 실행 전 프로젝트 루트에 `.accounts.json`(카카오 계정 이메일 목록)과 `.kauth.json`(REST API key·client_secret 등 OAuth 설정) 두 파일을 생성해야 한다.

## 필요 키 · 환경변수

| 항목 | 발급처 | 필수 |
|------|--------|------|
| REST API key (`.kauth.json`의 `client_id`) | [카카오 개발자센터](https://developers.kakao.com) | ✅ |
| client_secret (`.kauth.json`) | 카카오 애플리케이션 | ⬜ (임의 문자열도 동작) |

키는 환경변수가 아니라 `.kauth.json` / `.accounts.json` 파일로 주입한다. 카카오 로그인 활성화, 동의항목(닉네임·이메일·메시지 전송) 설정, 톡캘린더 사용 권한 신청이 선행되어야 한다.

## 설정 예시

```json
{
  "mcpServers": {
    "mcp-kakao": {
      "command": "uv",
      "args": ["--directory", "your-project-path/kakao-bot-mcp-server", "run", "mcp-kakao"]
    }
  }
}
```

## 비고

- 카카오가 공식 제공/유지보수하는 저장소가 아니며, 대부분의 API가 사업자등록 포함 비즈니스 애플리케이션 단위로 권한을 관리하므로 개인 사용은 제한적이다(README 명시).
- 작성 시점 기준 카카오톡 메시지는 '나에게 보내기' 기본 템플릿만, 톡캘린더는 목록 조회·서브 캘린더 관리만 지원된다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
