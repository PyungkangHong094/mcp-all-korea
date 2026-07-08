# naver-works-mcp

> **[hyeri0903/naver-works-mcp](https://github.com/hyeri0903/naver-works-mcp)** · ⭐ N/A (API rate limit) · Python · 최근 푸시 N/A · 카테고리: 🤝 Collaboration & Communication

네이버 웍스(Naver Works) API를 연동해 업무·카테고리·캘린더 일정을 관리하는 MCP 서버입니다.

## 개요

네이버 웍스(Naver Works) API를 연동하는 Python 기반 MCP 서버다. 개인 업무(task) 조회·생성·삭제, 업무 카테고리 관리, 기본 캘린더 일정 조회·생성·삭제, 개인 캘린더 목록 관리 기능을 제공한다. 로컬 실행과 Docker 이미지(`haileyjung/naverworks`) 두 가지 방식을 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `get_my_tasks` | 내 업무 목록 조회 (상태·필터 지정) |
| `create_my_task` | 새 업무 생성 |
| `delete_my_task` | 업무 삭제 |
| `get_my_categories` | 내 업무 카테고리 조회 |
| `delete_my_category` | 업무 카테고리 삭제 |
| `get_default_calendar_events` | 기본 캘린더 일정 조회 |
| `create_default_calendar_event` | 기본 캘린더 일정 생성 |
| `delete_default_calendar_event` | 기본 캘린더 일정 삭제 |
| `get_calendar_personal_user_list` | 개인 캘린더 목록 조회 |
| `create_calendar` | 캘린더 생성 |
| `delete_calendar` | 캘린더 삭제 |

## 설치

```bash
python3 -m venv venv
source venv/bin/activate
pip install 'mcp[cli]' httpx
# 또는 requirements.txt
pip install -r requirements.txt
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `WORKS_API_TOKEN` | [Naver Works Developers](https://developers.worksmobile.com) API 토큰 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-works-mcp": {
      "command": "{python path}",
      "args": ["{main.py file path}"],
      "env": {
        "WORKS_API_TOKEN": "{TOKEN}"
      }
    }
  }
}
```

Docker 이미지(`haileyjung/naverworks:latest`) 실행도 지원한다.

## 비고

- README 상단에 "Requesting removal from LobeHub listing" 문구가 있어 저자가 외부 목록 노출을 원치 않는 상태로 보인다.
- GitHub 메타데이터는 수집 시점 API rate limit으로 별점·푸시일 미확보.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(main.py)*
