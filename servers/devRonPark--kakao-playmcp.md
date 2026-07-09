# kakao-playmcp

> **[devRonPark/kakao-playmcp](https://github.com/devRonPark/kakao-playmcp)** · ⭐ N/A · Node.js/TypeScript · 최근 푸시 미상 · 카테고리: 🔤 Korean NLP & Language

한국어 카카오톡 문장을 자연스러운 일본어로 변환·교정하고 학습 카드를 제공하는 일본어 코치 MCP 서버입니다.

## 개요

"하루톡 일본어 코치" MCP 서버로, 한국어 카카오톡 문장을 자연스러운 일본어로 변환하고 초급 학습자를 위한 발음(Hepburn 로마자)·표현 설명·복습 카드·퀴즈를 제공한다. Anthropic API를 백엔드로 사용하며(환경변수 `ANTHROPIC_API_KEY` 필요), 모든 일본어 문장은 일본어 원문 → 로마자 발음 → 한국어 뜻 3단 구조로 반환한다. 번역·교정·표현설명·복습카드 저장·퀴즈 생성 5개 도구를 제공한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `translate_kakao_message` | 한국어 → 자연스러운 일본어 변환(로마자 발음·표현 분해·말투별 대안). 인자: `korean_text`(필수), `relationship`, `tone`, `learner_level` |
| `correct_japanese_sentence` | 일본어(또는 로마자) 문장 교정·이유 설명. 인자: `user_sentence`(필수), `intended_meaning`, `learner_level` |
| `explain_expression` | 일본어 표현을 초급자용으로 설명(예문·로마자). 인자: `expression`(필수), `context`, `learner_level` |
| `create_review_card` | 표현을 복습 카드로 저장. 인자: `expression`, `romanization`, `korean_meaning`, `difficulty` |
| `generate_daily_quiz` | 저장된 복습 카드로 1분 퀴즈 생성. 인자: `quiz_count`, `focus`, `level`, `reveal_answers` |

## 설치

```bash
git clone https://github.com/your-repo/kakao-playmcp.git
cd kakao-playmcp
npm install
npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `ANTHROPIC_API_KEY` | [Anthropic Console](https://console.anthropic.com) | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "harutalk-japanese-coach": {
      "command": "node",
      "args": ["/absolute/path/to/kakao-playmcp/dist/index.js"],
      "env": {
        "ANTHROPIC_API_KEY": "sk-ant-..."
      }
    }
  }
}
```

## 비고

- 라이선스 MIT.
- 번역·교정·설명 로직에 Anthropic API를 사용하므로 API 사용료 발생 가능.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
