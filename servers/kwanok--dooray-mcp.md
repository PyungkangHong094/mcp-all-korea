# dooray-mcp

> **[kwanok/dooray-mcp](https://github.com/kwanok/dooray-mcp)** · ⭐ N/A (API rate limit) · Python · 최근 푸시 N/A · 카테고리: 🤝 Collaboration & Communication

Dooray 업무·댓글·마일스톤·태그·템플릿·멤버·메신저 기능을 포함한 다수(README 표기 32개, 레퍼런스 명시 35개) 도구를 제공하는 MCP 서버입니다.

## 개요

Dooray 프로젝트 관리와 메신저를 통합하는 Python 기반 MCP 서버로, pip 패키지(`dooray-mcp`)로 배포된다. 태스크 CRUD·워크플로 변경, 댓글, 프로젝트, 마일스톤 CRUD, 태그, 포스트 템플릿 CRUD, 멤버 검색·프로젝트 멤버 관리, 메신저 채널·DM 기능을 32개 도구로 제공한다. MCP 서버와 CLI를 모두 지원한다.

## 제공 도구

README 제목은 32개로 표기하나 `docs/tools-reference.md`에는 아래 35개가 명시되어 있다(도메인별):

- **Task(6)**: `dooray_list_tasks`, `dooray_get_task`, `dooray_create_task`, `dooray_update_task`, `dooray_set_task_workflow`, `dooray_set_task_done`
- **Comment(4)**: `dooray_list_comments`, `dooray_add_comment`, `dooray_update_comment`, `dooray_delete_comment`
- **Project(2)**: `dooray_get_project`, `dooray_list_workflows`
- **Milestone(5)**: `dooray_list_milestones`, `dooray_get_milestone`, `dooray_create_milestone`, `dooray_update_milestone`, `dooray_delete_milestone`
- **Tag(3)**: `dooray_list_tags`, `dooray_get_tag`, `dooray_create_tag`
- **Template(5)**: `dooray_list_templates`, `dooray_get_template`, `dooray_create_template`, `dooray_update_template`, `dooray_delete_template`
- **Member(4)**: `dooray_search_members`, `dooray_list_project_members`, `dooray_get_project_member`, `dooray_add_project_member`
- **Messenger(6)**: `dooray_list_channels`, `dooray_create_channel`, `dooray_send_channel_message`, `dooray_send_direct_message`, `dooray_join_channel_members`, `dooray_leave_channel_members`

## 설치

```bash
pip install dooray-mcp
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DOORAY_API_KEY` | Dooray! 개인 인증 토큰 | ✅ |

`.env` 파일로 설정한다.

## 설정 예시

```json
{
  "mcpServers": {
    "dooray": {
      "command": "dooray-mcp"
    }
  }
}
```

## 비고

- CLI도 제공(`dooray task/comment/project/milestone/member/messenger ...`).
- 도구 상세는 `docs/tools-reference.md` 참조.
- GitHub 메타데이터는 수집 시점 API rate limit으로 별점·푸시일 미확보.

---
*수집일: 2026-07-02 · 출처: 저장소 README, docs/tools-reference.md*
