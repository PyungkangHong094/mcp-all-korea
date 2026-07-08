# AgentWebSearch-MCP

> **[insung8150/AgentWebSearch-MCP](https://github.com/insung8150/AgentWebSearch-MCP)** · ⭐ 12 · Python · 최근 푸시 2026-02-19 · 카테고리: 🔎 Search & Trends

API 키 없이 Chrome 브라우저(CDP)로 네이버·구글·Brave를 병렬 검색하는 로컬 웹서치 MCP 서버입니다.

## 개요

로컬 LLM(Ollama, LM Studio)이나 Claude Code에서 웹 검색을 쓸 수 있게 해주는 MCP 서버다. 헤드리스가 아닌 실제 Chrome 창을 CDP(Chrome DevTools Protocol)로 제어하여 네이버·구글·Brave를 동시에 검색한다. 실제 브라우저 세션을 쓰기 때문에 API 키·rate limit이 없고, 봇 탐지·CAPTCHA에 강하며 네이버 같은 한국 포털도 지원한다. 포트 9222/9223/9224에 각각 Chrome 인스턴스를 띄워 병렬 검색한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `web_search` | 네이버/구글/Brave 병렬 검색 |
| `fetch_urls` | URL에서 웹페이지 본문 가져오기 |
| `smart_search` | 검색 + 깊이 제어 자동 페치 |
| `get_search_status` | 검색 진행 상황·부분 결과 확인 |
| `cancel_search` | 진행 중 검색 취소·부분 결과 반환 |
| `agentcpm` | AgentCPM-Explore(SGLang) 기반 에이전트 검색 (별도 LLM 필요) |

## 설치

```bash
git clone https://github.com/insung8150/AgentWebSearch-MCP.git
cd AgentWebSearch-MCP
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt

# Chrome 디버깅 인스턴스 3개 기동 후 MCP 서버 실행
python chrome_launcher.py start
python mcp_server.py
```

## 필요 키 · 환경변수

API 키 불필요 (실제 Chrome 브라우저를 직접 제어). 단, 사전에 Chrome 설치와 `chrome_launcher.py start`로 CDP 인스턴스 기동이 필요하다.

## 설정 예시

```json
{
  "mcpServers": {
    "agentwebsearch": {
      "command": "python",
      "args": ["/path/to/AgentWebSearch-MCP/mcp_server.py"],
      "env": {}
    }
  }
}
```

## 비고

- MCP 서버 실행 전 반드시 `python chrome_launcher.py start`로 Chrome CDP 인스턴스를 먼저 띄워야 한다.
- SSE(HTTP) 모드 지원: `python mcp_server.py --sse --port 8902`.
- `agentcpm` 도구만 별도 LLM(AgentCPM-Explore 4B, SGLang)이 필요하고 나머지 도구는 불필요.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
