# KERIS_EDUmcp

> **[Won-ahamada/KERIS_EDUmcp](https://github.com/Won-ahamada/KERIS_EDUmcp)** · ⭐ N/A (GitHub API 제한) · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

학교알리미 API(17종)와 RISS 학술 API를 TOON 파일로 확장하는 18개 도구 한국 교육데이터 MCP 서버입니다.

## 개요

확장 가능한 교육 API 통합 MCP 서버다. `.toon`(Token-Oriented Object Notation) 파일을 `providers/` 폴더에 넣으면 서버 시작 시 자동 스캔되어 각 API 엔드포인트가 MCP 도구로 등록되는 플러그인 아키텍처를 갖는다. 기본 제공 Provider는 교육부 학교알리미(엔드포인트 12개 → 도구 17개)와 한국교육학술정보원 RISS 학위논문 검색(도구 1개)이며, 총 18개 도구가 등록된다. stdio 모드 외에 HTTP(JSON-RPC 2.0, 기본 `:3000`) 모드도 지원한다.

## 제공 도구

| 항목 | 내용 |
|------|------|
| 학교알리미 (school-alrimi) | 엔드포인트 12개 / MCP 도구 17개 |
| RISS (riss) | 학위논문 검색 / MCP 도구 1개 |
| **합계** | **18개 도구** |

> 도구는 TOON 파일에서 런타임에 동적 생성되며, README에 개별 도구명이 표로 명시되어 있지 않아 여기서는 Provider·개수 단위로 기록한다 (개별 도구명: 저장소 README에 명시 없음).

## 설치

```bash
git clone https://github.com/Won-ahamada/KERIS_EDUmcp.git
cd KERIS_EDUmcp
npm install
npm run build   # dist/index.js 생성
```

- 요구사항: Node.js >= 20.0.0

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `SCHOOL_ALRIMI_API_KEY` | [학교알리미](https://www.schoolinfo.go.kr) | 권장 |
| `RISS_API_KEY` | [RISS](https://www.riss.kr) | 권장 |

## 설정 예시

```json
{
  "mcpServers": {
    "edu-api": {
      "command": "node",
      "args": ["/absolute/path/to/KERIS_EDUmcp/dist/index.js"],
      "env": {
        "SCHOOL_ALRIMI_API_KEY": "your_key_here",
        "RISS_API_KEY": "your_key_here"
      }
    }
  }
}
```

## 비고

- 라이선스: MIT.
- HTTP 버전(`npm run start:http`)으로 웹 애플리케이션 통합 및 Fly.io/Railway 원격 배포를 지원한다.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
