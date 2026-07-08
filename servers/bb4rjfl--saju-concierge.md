# saju-concierge

> **[bb4rjfl/saju-concierge](https://github.com/bb4rjfl/saju-concierge)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 🧩 Miscellaneous

생년월일시로 사주 명식을 계산해 운세·궁합·이름풀이·타로를 제공하는 MCP 서버.

## 개요

생년월일시를 입력받아 사주 명식(4기둥)과 오행 분포를 계산하고, 오늘의 기운·올해 운세·궁합·성향 분석·이름풀이·타로를 엔터테인먼트 톤으로 풀어준다. 명식 계산은 검증된 MIT 라이브러리 `manseryeok-js`(`@fullstackfamily/manseryeok`)에 맡기고, 해석은 자체 명리학 데이터 + LLM 표현으로 차별화한다. 카카오 Agentic Player 10 / PlayMCP 공모전 출품작이며 Streamable HTTP · Remote · Stateless 원격 MCP로 설계됐다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `computeSajuChart` | 생년월일시 → 명식(4기둥) + 오행분포 계산·표시 (기반 툴) |
| `getTodayFortune` | 오늘의 기운/운세 (일진 대비 명식) |
| `getYearlyFortune` | 올해/특정 연도 운세 흐름 (세운·대운 개략) |
| `getCompatibility` | 두 사람 궁합 (명식 2개 비교) |
| `analyzePersonality` | 타고난 성향 분석 (십신·오행 균형 기반) |
| `interpretName` | 이름풀이 (한글/한자 획수·오행, 자체 규칙) |
| `drawTarot` | 타로 한 장/스프레드 뽑기 + 의미 (보조 엔터 기능) |

## 설치

npm 미배포. TypeScript + `@modelcontextprotocol/sdk`(Streamable HTTP, stateless)로 구현되며 Dockerfile(linux/amd64)로 빌드해 카카오 클라우드 PlayMCP(KC)에 배포한다. 소스 빌드형.

## 필요 키 · 환경변수

README에 API 키·환경변수 명시 없음. 명식 계산은 로컬 라이브러리(`manseryeok-js`)로 수행되어 외부 API 키가 필요 없어 보인다.

## 설정 예시

원격 Streamable HTTP MCP로, PlayMCP 콘솔에서 발급된 엔드포인트 URL에 연결한다.

```json
{
  "mcpServers": {
    "saju-concierge": {
      "url": "<PlayMCP에서 발급된 엔드포인트 URL>"
    }
  }
}
```
(README 기반 구성)

## 비고

- 도구 목록은 `docs/02_product_spec.md`·`docs/03_tool_contracts.md`에서 확인(7개).
- 카카오 PlayMCP 규칙 준수: 서버명·툴명에 `kakao` 금지, 툴 3~10개, 영문 description, 응답 Markdown ≤24k, p99 3s, 생년월일 미저장.
- 운세는 엔터테인먼트 톤(단정·공포 금지) + 면책 문구.

---
*수집일: 2026-07-02 · 출처: 저장소 README, docs/02·03*
