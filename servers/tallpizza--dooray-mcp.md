# dooray-mcp

> **[tallpizza/dooray-mcp](https://github.com/tallpizza/dooray-mcp)** · ⭐ N/A (GitHub API rate-limit) · Python · 카테고리: 🤝 Collaboration & Communication

Dooray API를 6개 통합 도구로 묶어 업무·댓글·태그·검색을 관리하는 MCP 서버입니다.

## 개요

협업 도구 Dooray의 API를 Claude Code 등 MCP 클라이언트와 연동하는 서버다. 업무·댓글·태그·검색·사용자·파일 관리를 6개의 통합 도구로 제공하며, 각 도구는 `action`/`searchType` 인자로 여러 오퍼레이션(목록·상세·생성·수정·삭제 등)을 분기한다. 본문 이미지 업로드용 S3 호환 스토리지를 선택적으로 연동할 수 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `dooray_tasks` | 업무 관리 (목록·상세·생성·수정·삭제·상태변경·담당자 지정) |
| `dooray_comments` | 댓글 관리 (목록·생성·수정·삭제, 멘션 지원) |
| `dooray_tags` | 태그 관리 (목록·생성, 업무 태그 추가/제거) |
| `dooray_search` | 검색 (업무·담당자별·상태별·태그별·기간별) |
| `dooray_members` | 사용자 관리 (이메일/ID 검색, 정보 조회, 프로젝트 멤버 목록) |
| `dooray_files` | 파일·이미지 관리 (업로드/목록, S3 본문 이미지 업로드, 메타데이터, 다운로드) |

## 설치

저장소 클론 후 `uv sync`로 의존성 설치, `uv run python -m dooray_mcp.server`로 실행.

```bash
git clone https://github.com/tallpizza/dooray-mcp.git
cd dooray-mcp
uv sync
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `DOORAY_API_TOKEN` | Dooray 개인/프로젝트 API 토큰 | ✅ |
| `DOORAY_DEFAULT_PROJECT_ID` | 기본 프로젝트 ID | ✅ |
| `DOORAY_BASE_URL` | API 베이스 URL(`https://api.dooray.com`) | ❌ |
| `S3_BUCKET` / `S3_REGION` / `S3_ACCESS_KEY_ID` / `S3_SECRET_ACCESS_KEY` | 본문 이미지 업로드용 S3 호환 스토리지 | ❌ (`upload_body_image` 사용 시) |

## 설정 예시

```json
{
  "type": "stdio",
  "command": "uv",
  "args": ["run", "python", "-m", "dooray_mcp.server"],
  "env": {
    "DOORAY_API_TOKEN": "your-actual-dooray-api-token",
    "DOORAY_BASE_URL": "https://api.dooray.com",
    "DOORAY_DEFAULT_PROJECT_ID": "your-default-project-id"
  }
}
```

## 비고

`claude mcp add-json`으로 등록하는 흐름을 README에서 안내. S3 연동은 본문 이미지용으로만 선택 사용. 도구 목록은 README에 명시.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
