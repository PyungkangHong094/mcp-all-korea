# kolas-mcp

> **[vertical-mcp/kolas-mcp](https://github.com/vertical-mcp/kolas-mcp)** · ⭐ N/A · TypeScript · 카테고리: 📊 Public Data

국가기술표준원(KATS) 산하 KOLAS 공인 교정·시험·검사 기관 정보를 검색하는 MCP 서버입니다.

## 개요

한국인정기구(KOLAS, Korean Laboratory Accreditation Scheme)의 공개 데이터를 래핑한 TypeScript MCP 서버다. KATS(국가기술표준원) 산하 인정기관 포털(knab.go.kr)의 HTML을 파싱해 교정·시험·검사·의료시험·표준물질생산·숙련도시험 인정기관을 검색하고, 공공데이터포털(data.go.kr) 데이터셋 15054300으로 연도별 인정현황 통계를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `search_accredited_labs` | 자유 텍스트 질의 + 카테고리(CALIBRATION/TESTING/INSPECTION/MEDICAL/REFERENCE/PROFICIENCY/ALL)로 인정기관 검색. API 키 불필요 |
| `get_lab_details` | 인정번호(예: `KT001`)로 단일 기관 상세(인정범위·이력·연락처) 조회. API 키 불필요 |
| `get_kolas_statistics` | 카테고리별 연간 인정 건수(데이터셋 15054300). `KOLAS_SERVICE_KEY` 필요 |

## 설치

```bash
npx @vertical-mcp/kolas-mcp
```

또는 전역 설치: `npm install -g @vertical-mcp/kolas-mcp && kolas-mcp`

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOLAS_SERVICE_KEY` | [공공데이터포털 data.go.kr](https://www.data.go.kr/data/15054300/fileData.do) 데이터셋 15054300 | 선택 |

기관 검색(`search_accredited_labs`, `get_lab_details`)은 키 없이 동작하며, 통계 도구(`get_kolas_statistics`)에만 키가 필요하다.

## 설정 예시

```json
{
  "mcpServers": {
    "kolas-mcp": {
      "command": "npx",
      "args": ["-y", "@vertical-mcp/kolas-mcp"],
      "env": {
        "KOLAS_SERVICE_KEY": "your-optional-data.go.kr-key"
      }
    }
  }
}
```

## 비고

- 인정번호 접두어로 카테고리 자동 추론: `KC` 교정, `KT` 시험, `KI` 검사, `KM` 의료시험, `KR` 표준물질생산, `KP` 숙련도시험.
- `search_accredited_labs`/`get_lab_details`는 knab.go.kr HTML을 파싱하므로 포털 개편 시 셀렉터가 깨질 수 있다.
- KATS/KOLAS/MOTIE와 무관한 비공식 커뮤니티 래퍼. 라이선스 MIT © 2026 Yongbum Kim.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
