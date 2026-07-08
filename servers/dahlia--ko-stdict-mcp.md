# ko-stdict-mcp

> **[dahlia/ko-stdict-mcp](https://github.com/dahlia/ko-stdict-mcp)** · ⭐ 25 · TypeScript · 최근 푸시 2026-03-29 · 카테고리: 🔤 Korean NLP & Language

표준국어대사전 전체 데이터를 SQLite에 저장해 레이트 리미트 없이 표제어·뜻풀이·발음·용례를 빠르게 조회하는 MCP 서버입니다.

## 개요

국립국어원 《표준국어대사전》의 공식 "사전 내려받기" JSON 덤프를 내려받아 SQLite로 정규화한 뒤 조회하는 Deno 기반 stdio MCP 서버다. 최초 기동 시 공식 덤프를 다운로드해 로컬 DB를 구성하고, 이후에는 캐시된 ZIP과 정규화 DB를 재사용한다. Open API 키 없이 동작하며 레이트 리미트가 없다. 조회 시 필요한 필드만 선택할 수 있다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_entries` | 표제어 exact/prefix/contains 검색 |
| `get_entry` | `target_code` 기반 상세 조회 |
| `dictionary_status` | 로컬 데이터 상태 조회 |
| `refresh_dictionary` | 공식 덤프를 다시 받아 DB 갱신 |

## 설치

```bash
deno install
deno task dev     # 실행
deno task init    # 초기 데이터만 준비
deno task refresh # 강제 재구성
```

JSR 배포판(`jsr:@hongminhee/ko-stdict-mcp`)으로도 실행 가능하다.

## 필요 키 · 환경변수

API 키 불필요. (국립국어원 Open API 키 없이 동작)

| 환경변수 | 용도 | 필수 |
|---------|------|------|
| `KO_STDICT_DATA_DIR` | 데이터 저장 경로 변경(기본: `$XDG_DATA_HOME/ko-stdict-mcp`) | ❌ |

## 설정 예시

```json
{
  "mcpServers": {
    "ko-stdict": {
      "command": "deno",
      "args": ["run", "-A", "jsr:@hongminhee/ko-stdict-mcp"]
    }
  }
}
```

## 비고

- 요구사항: Deno 2.0 이상.
- 라이선스: AGPL-3.0.
- 데이터 저작권·이용조건은 국립국어원 원 제공처 정책을 따른다.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
