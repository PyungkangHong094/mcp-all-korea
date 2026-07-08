# assembly-api-mcp

> **[hollobit/assembly-api-mcp](https://github.com/hollobit/assembly-api-mcp)** · ⭐ 81 · TypeScript · 최근 푸시 2026-05-02 · 카테고리: 📜 Legal & Government

대한민국 국회 Open API + 국민참여입법센터 + NABO를 통합한 MCP 서버 — 287개 API 접근.

## 개요

대한민국 국회 관련 Open API(276개 국회 + 8개 국민참여입법센터 + 3개 국회예산정책처 NABO)를 MCP로 노출한다. 국회의원, 의안, 일정, 회의록, 위원회, 표결, 청원, 입법현황/예고, NABO 보고서까지 도메인 엔티티 기반으로 통합했다. Lite(6개)/Full(11개) 두 프로필을 제공하며, 통합 도구로 못 다루는 API는 `discover_apis`·`query_assembly` 범용 도구로 즉시 호출한다. stdio(Claude Desktop) + HTTP(원격) 이중 Transport, REST API + OpenAPI 스펙(ChatGPT GPTs Actions)도 지원.

## 제공 도구

| 도구 | 기능 | 프로필 |
|------|------|------|
| `assembly_member` | 국회의원 조회·분석(역대·정당 통계·영문 포함) | Lite |
| `assembly_bill` | 의안 조회·입법 추적(ALLBILL 심사경과 포함) | Lite |
| `assembly_session` | 일정·회의록·표결 조회 | Lite |
| `assembly_org` | 위원회·청원·입법예고·보도자료(`type=lawmaking/press`) | Lite |
| `discover_apis` | 287개 API 탐색 | Lite |
| `query_assembly` | 임의 국회 API 범용 호출 | Lite |
| `bill_detail` | 의안 상세(심사경과·제안자·심사보고) | Full |
| `research_data` | 국회도서관·연구보고서·예산분석 통합 | Full |
| `get_nabo` | 국회예산정책처 자료(`type=report/periodical/recruitments`) | Full |
| `committee_detail` / `petition_detail` | 위원회·청원 상세 | Full |

## 설치

```bash
# 자동 설치 마법사(권장) — Node.js 18+
npx assembly-api-mcp setup
```

원격 서버(설치 불필요) 방식도 지원한다.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| 국회 API 키 | [open.assembly.go.kr](https://open.assembly.go.kr) (무료, `sample` 키로 테스트 가능) | ✅ |
| 국민참여입법센터 OC | [opinion.lawmaking.go.kr](https://opinion.lawmaking.go.kr) (정보공개 서비스 신청) | ❌(lawmaking API 사용 시) |
| NABO API 키 | [nabo.go.kr](https://www.nabo.go.kr/ko/api/apply.do) | ❌(NABO 사용 시) |

## 설정 예시

```bash
# 대화형 마법사가 API 키 입력 → 프로필 선택 → 클라이언트 설정을 자동 처리
npx assembly-api-mcp setup
```

(README 기반 구성 — 마법사가 `claude_desktop_config.json`을 자동 생성)

## 비고

- MIT 라이선스. macOS·Windows·Linux 동일 명령. Lite/Full 프로필로 노출 도구 수를 조절.
- v0.4에서 도구 구조가 대규모 통합(Breaking Change)됨 — 구버전 도구명은 매핑 문서 참조.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
