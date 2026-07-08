# be-node-seoul-data-mcp

> **[pinnaclesoft-ko/be-node-seoul-data-mcp](https://github.com/pinnaclesoft-ko/be-node-seoul-data-mcp)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

서울시 공공데이터 API를 조회하는 MCP 서버 예제입니다.

## 개요

서울 열린데이터광장(openapi.seoul.go.kr) API를 MCP로 노출하는 **예제(sample) 프로젝트**. 두 가지 데이터를 다룬다: 서울시 지하철호선별 역별 승하차 인원 정보, 서울시 문화행사 정보. TypeScript로 작성되어 `npm run build` 후 Node로 실행한다.

## 제공 도구

도구 이름은 README에 명시되지 않음. 다루는 데이터(예제 목록):
- 서울시 지하철호선별 역별 승하차 인원 정보 (`modules/KoreaSeoulSubwayStatus.ts`)
- 서울시 문화행사 정보 (`modules/KoreaSeoulCulturalEventInfo.ts`)

(정확한 도구명은 소스의 각 module 파일에서 확인 필요 — README에는 미기재)

## 설치

```bash
npm i
npm run build
```

## 필요 키 · 환경변수

서울 열린데이터광장 인증키가 필요하나, **환경변수가 아니라 소스 파일에 직접 하드코딩**한다:
- `modules/KoreaSeoulCulturalEventInfo.ts`의 `const API_KEY = "{API 키}"`
- `modules/KoreaSeoulSubwayStatus.ts`의 `const API_KEY = "{API 키}"`

키 발급: [서울 열린데이터광장](https://data.seoul.go.kr) (`openapi.seoul.go.kr:8088` 인증키)

## 설정 예시

```json
{
  "mcpServers": {
    "KoreaSeoulData": {
      "command": "node",
      "args": ["{빌드된 경로}/seoul_korea/dist/index.js"]
    }
  }
}
```

## 비고

교육용 예제 프로젝트다. API 키를 환경변수가 아닌 소스에 직접 삽입하는 구조라 실사용 시 주의. 도구명은 README에 없어 소스 확인이 필요하다.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
