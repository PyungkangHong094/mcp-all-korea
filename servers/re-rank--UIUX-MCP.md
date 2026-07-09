# UIUX-MCP

> **[re-rank/UIUX-MCP](https://github.com/re-rank/UIUX-MCP)** · ⭐ N/A (GitHub API 제한) · TypeScript · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

정부 표준 디자인시스템 KRDS 컴포넌트 검색·HTML 코드 삽입·디자인토큰 조회·접근성/준수 검증을 제공하는 9개 도구 MCP 서버입니다.

## 개요

대한민국 디지털 정부 표준 디자인 시스템인 **KRDS(Korea Responsive Design System)**를 AI 어시스턴트와 통합하는 MCP 서버다. npm 패키지 `krds-uiux`를 데이터 소스로 사용하여 65개 이상의 KRDS HTML 컴포넌트 검색, 즉시 사용 가능한 코드 스니펫 제공, 디자인 토큰(색상·간격·타이포그래피) 조회, HTML/CSS 코드의 KRDS 가이드라인·접근성 준수 검증을 수행한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_krds_components` | 키워드·카테고리로 KRDS 컴포넌트 검색 |
| `get_component_code` | 특정 컴포넌트의 전체 HTML 코드 조회 |
| `list_component_categories` | 컴포넌트 카테고리 목록 조회 |
| `list_all_components` | 전체 컴포넌트 이름 목록 조회 |
| `search_design_tokens` | 디자인 토큰 검색 (type/query) |
| `get_color_palette` | 전체 색상 팔레트 조회 |
| `get_token_stats` | 디자인 토큰 통계 조회 |
| `validate_krds_compliance` | HTML/CSS 코드의 KRDS 준수 검증·개선 제안 |
| `get_krds_resources` | 리소스 파일(css/scss/fonts/images/js) 경로 조회 |

## 설치

```bash
# Smithery
npx @smithery/cli install krds-uiux-mcp-server

# 수동 빌드
git clone https://github.com/re-rank/UIUX-MCP
cd UIUX-MCP
npm install
npm run build   # build/index.js 생성
```

## 필요 키 · 환경변수

API 키 불필요.

## 설정 예시

```json
{
  "mcpServers": {
    "krds-uiux": {
      "command": "node",
      "args": ["/absolute/path/to/UIUX-MCP/build/index.js"]
    }
  }
}
```

## 비고

- 라이선스: ISC.
- README의 설정 예시가 작성자 개인 절대경로(`C:/Users/박호진/...`)로 되어 있어, 위 예시는 빌드 산출물 경로를 일반화한 것이다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
