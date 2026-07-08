# py-mcp-naver-search

> **[jikime/py-mcp-naver-search](https://github.com/jikime/py-mcp-naver-search)** · ⭐ 4 · Python · 최근 푸시 2025-05-06 · 카테고리: 🔎 Search & Trends

네이버 검색 API로 다양한 콘텐츠 검색 결과를 LLM이 처리하기 쉬운 구조화 텍스트로 제공하는 Python MCP 서버.

## 개요

네이버 검색 API에 접근해 블로그·뉴스·책·이미지·쇼핑 등 여러 유형의 콘텐츠를 검색하는 Python MCP 서버다. 페이지네이션을 지원하고, 결과를 LLM 소비에 최적화된 구조화 텍스트로 반환한다. 성인 콘텐츠 판별과 키보드 입력 오류 교정(errata) 기능도 제공한다. 총 13개 검색 카테고리를 지원한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_blog` | 블로그 검색 (display·page·sort 파라미터) |
| `search_news` | 뉴스 검색 |
| `search_book` | 책 정보 검색 |
| `check_adult_query` | 성인 검색어 여부 판별 |
| `search_encyclopedia` | 백과사전 검색 |
| `search_cafe_article` | 카페 글 검색 |
| `search_kin` | 지식iN Q&A 검색 |
| `search_local` | 지역 업체 정보 검색 |

추가 지원 카테고리(클라이언트 기준): `shop`(쇼핑), `doc`(학술/문서), `image`(이미지), `webkr`(웹), `errata`(오타 교정). 총 13개 카테고리.

## 설치

```bash
git clone https://github.com/jikime/py-mcp-naver-search.git
cd py-mcp-naver-search
uv venv -p 3.12
source .venv/bin/activate
pip install -r requirements.txt
# 실행: mcp run server.py   (또는 Docker: docker build -t py-mcp-naver-search . && docker run ...)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [Naver Developers](https://developers.naver.com/apps/#/register) | ✅ |
| `NAVER_CLIENT_SECRET` | Naver Developers | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "naver-search": {
      "command": "/path/to/bin/uv",
      "args": [
        "--directory", "/path/to/py-mcp-naver-search",
        "run", "server.py"
      ]
    }
  }
}
```

## 비고

- Python 3.12+ 필요. Smithery(`@smithery/cli install @jikime/py-mcp-naver-search`)로 자동 설치 가능, Docker 실행도 지원.
- 라이선스 파일 존재(MIT, README 배지 명시), GitHub API에는 license 미표기.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
