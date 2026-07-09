# KatokMCP

> **[mwl313/KatokMCP](https://github.com/mwl313/KatokMCP)** · ⭐ N/A (GitHub API rate-limit) · TypeScript · 카테고리: 🤝 Collaboration & Communication

카카오톡을 제어해 대화 읽기·메시지 전송·채팅방 목록 관리를 수행하는 MCP 서버입니다.

## 개요

카카오톡의 비공개 프로토콜(LOCO)을 분석해 구현한 오픈소스 MCP 서버다. AI 비서가 채팅방 목록·읽지 않은 메시지·멤버를 조회하고 메시지를 읽거나 대신 전송할 수 있다. 최초 1회 휴대폰 인증이 필요하며, 계정 정보는 AES-256-GCM으로 암호화 저장된다. 메시지 전송은 기본 비활성화이고 `KAKAO_ALLOW_WRITE=YES` 설정 시에만 가능하며, AI가 보낸 메시지에는 자동으로 🤖 표식이 붙는다. 카카오 공식·제휴 프로젝트가 아니며 연구·교육 목적으로만 사용을 권고한다.

## 제공 도구

소스(`packages/mcp-server/src/index.ts`)에서 등록되는 도구 4개.

| 도구 | 기능 |
|------|------|
| `kakao_list_chats` | 채팅방 목록·읽지 않은 메시지 수·멤버·마지막 메시지 |
| `kakao_read_chat` | 특정 채팅방 최근 메시지 내역 읽기 |
| `kakao_send_chat` | 메시지 전송 (opt-in 필수, 🤖 표식 자동) |
| `kakao_list_members` | 채팅방 멤버 조회 |

## 설치

Node.js 18 이상 필요. 글로벌 설치 후 설치 마법사를 실행하거나 npx로 실행한다.

```bash
npm install -g @katok-mcp/mcp-server
katok-mcp setup
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KAKAO_EMAIL` | 카카오톡 계정 이메일 | ✅ |
| `KAKAO_PASSWORD` | 카카오톡 계정 비밀번호 | ✅ |
| `KAKAO_ANDROID_DEVICE_UUID` | Device UUID (마법사가 자동 생성) | ✅ |
| `KAKAO_ALLOW_WRITE` | 메시지 전송 허용(`YES`) | ❌ (전송 시 필요) |

`katok-mcp setup` 사용 시 계정 정보는 암호화 저장되어 클라이언트 설정 파일에는 비밀번호가 남지 않는다.

## 설정 예시

```json
{
  "mcpServers": {
    "katok": {
      "command": "katok-mcp",
      "args": []
    }
  }
}
```

## 비고

비공식 프로젝트 — 카카오와 제휴/보증 관계 없음. LOCO 비공개 프로토콜 분석 기반, 연구·교육 목적 권고. 메시지 전송 기본 비활성화. 도구명은 소스에서 확인. 라이선스 MIT.

---
*수집일: 2026-07-03 · 출처: 저장소 README, 소스 코드(packages/mcp-server/src/index.ts)*
