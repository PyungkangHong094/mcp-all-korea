# mcp-korean-spell

> **[winterjung/mcp-korean-spell](https://github.com/winterjung/mcp-korean-spell)** · ⭐ 24 · TypeScript · 최근 푸시 2025-04-15 · 카테고리: 🔤 Korean NLP & Language

한국어 맞춤법과 문법 오류를 교정하는 도구를 제공하는 MCP 서버입니다.

## 개요

네이버 맞춤법 검사기를 백엔드로 삼아 한국어 텍스트의 맞춤법·문법 오류를 교정하는 TypeScript 기반 MCP 서버다. npm 패키지(`@winterjung/mcp-korean-spell`)로 배포되며, 글쓰기 도구에 맞춤법 검사 기능을 통합하는 용도다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `fix_korean_spell` | 한국어 텍스트의 맞춤법·문법 오류를 분석·교정 |

## 설치

```bash
npx -y @winterjung/mcp-korean-spell
```

## 필요 키 · 환경변수

API 키 불필요.

## 설정 예시

```json
{
  "mcpServers": {
    "korean-spell-checker": {
      "command": "npx",
      "args": ["-y", "@winterjung/mcp-korean-spell"]
    }
  }
}
```

## 비고

- 라이선스: Apache-2.0.
- 네이버 맞춤법 검사기의 비공식 활용이며, 서비스 제공사와 무관하다. 서비스 중단·변경 시 동작하지 않을 수 있다.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
