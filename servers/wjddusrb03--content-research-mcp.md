# content-research-mcp

> **[wjddusrb03/content-research-mcp](https://github.com/wjddusrb03/content-research-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-03-20 · 카테고리: 🔎 Search & Trends

네이버 트렌드·블로그·뉴스 검색과 파파고 번역, Unsplash 이미지를 한 번에 묶어 콘텐츠 리서치 보고서를 생성하는 MCP 서버입니다.

## 개요

콘텐츠 크리에이터용 리서치 MCP 서버(Python)다. 네이버 데이터랩 트렌드 + 블로그/뉴스 검색 + 파파고 번역 + Unsplash 이미지 4개 API를 하나의 파이프라인으로 결합해, 한 번의 도구 호출로 검색 트렌드·인기 블로그·최신 뉴스·무료 이미지를 담은 완성형 리서치 보고서를 생성한다. 미설정 API 키는 자동으로 스킵된다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `research_topic` | 핵심 기능. 트렌드+블로그+뉴스+이미지를 종합 리서치 보고서로 생성 |
| `trend_keywords` | 네이버 데이터랩으로 최대 5개 키워드 검색 트렌드 비교 |
| `search_blogs` | 네이버 블로그 인기 콘텐츠·글 방향 탐색 |
| `search_news` | 네이버 최신 뉴스 검색 |
| `translate_text` | 네이버 파파고 번역 (en/ko/ja/zh-CN 등) |
| `search_images` | Unsplash 무료 상업용 이미지 검색 |
| `api_status` | 설정된 API 확인 — 미설정 키 자동 스킵 |

## 설치

```bash
git clone https://github.com/wjddusrb03/content-research-mcp.git
cd content-research-mcp
pip install -r requirements.txt
python setup_wizard.py   # 대화형 자동 설치(권장). 수동 설치는 .env 직접 작성
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NAVER_CLIENT_ID` | [네이버 개발자센터](https://developers.naver.com) (트렌드·블로그·뉴스·번역) | ✅ |
| `NAVER_CLIENT_SECRET` | 네이버 개발자센터 | ✅ |
| `UNSPLASH_ACCESS_KEY` | [Unsplash Developers](https://unsplash.com/developers) (이미지) | ⬜ |

모든 API가 무료(신용카드 불필요). 미설정 키는 해당 기능만 스킵된다.

## 설정 예시

```json
{
  "mcpServers": {
    "content-research": {
      "command": "python",
      "args": ["/전체/경로/content-research-mcp/server.py", "--env", "/전체/경로/content-research-mcp/.env"]
    }
  }
}
```

## 비고

- `setup_wizard.py`가 API 키 입력, `.env` 생성, Claude Desktop 설정 등록, 기존 설정 백업을 자동 처리한다.
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
