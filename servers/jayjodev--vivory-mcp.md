# vivory-mcp

> **[jayjodev/vivory-mcp](https://github.com/jayjodev/vivory-mcp)** · ⭐ 0 · Python · 최근 푸시 2026-06-05 · 카테고리: 📊 Public Data

KOSIS 등 한국 공공데이터를 MCP 서버 패키지로 제공하는 Vivory 기반 프로젝트 (api.vivory.app 게이트웨이 경유).

## 개요

Vivory가 관리하는 한국 공공데이터 MCP 모노레포로, `vivory-mcp-kosis`(KOSIS 통계청)와 우산 패키지 `vivory-mcp-korea`(KOSIS + ECOS·NEIS·LOCALDATA 예정)를 PyPI로 배포한다. 각 패키지는 얇은 래퍼로, MCP 도구 호출을 `api.vivory.app`에 대한 HTTP GET으로 변환한다(캐싱·출처표기·정규화는 백엔드가 담당).

> ⚠️ **중요: 현재 두 패키지 모두 deprecated 상태다.** 소스(`packages/*/server.py`)를 확인한 결과, `api.vivory.app/api/public-tools/*` 게이트웨이가 2026-05-22부로 클러스터 내부용으로 전환되어 기존 KOSIS 도구가 프록시되지 않는다. 모든 도구 호출은 마이그레이션 안내(deprecation notice)만 반환한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `vivory_kosis_deprecated_migration_notice` | (kosis 패키지) deprecation·마이그레이션 안내 반환 |
| `vivory_korea_deprecated_migration_notice` | (umbrella 패키지) deprecation·마이그레이션 안내 반환 |

README는 "15개 KOSIS 도구"를 광고하나, 실제 소스에서는 위 안내 도구만 노출되고 구 KOSIS 도구명(호출 시)도 동일 안내를 반환한다.

## 설치

```bash
# PyPI (릴리스 대기 중일 수 있음)
uvx vivory-mcp-kosis
# 또는 git subdirectory
uvx --from "git+https://github.com/jayjodev/vivory-mcp.git#subdirectory=packages/mcp-server-kosis" vivory-mcp-kosis
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `VIVORY_API_BASE` | 자가 호스팅 백엔드 지정용(선택) | ❌ |

KOSIS 계정·API 키 불필요(백엔드가 처리). 단, 백엔드가 현재 비공개·내부용.

## 설정 예시

```json
{
  "mcpServers": {
    "vivory-kosis": {
      "command": "uvx",
      "args": ["vivory-mcp-kosis"]
    }
  }
}
```

## 비고

- 두 패키지 모두 deprecated. 실질 데이터 조회 불가, 마이그레이션 안내만 반환.
- Vivory 백엔드 코드는 비공개(private Vivory app monorepo).
- 라이선스: MIT(래퍼), KOSIS 데이터는 공공누리(KOGL) 1유형.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(server.py)*
