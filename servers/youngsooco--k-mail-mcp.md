# k-mail-mcp

> **[youngsooco/k-mail-mcp](https://github.com/youngsooco/k-mail-mcp)** · ⭐ (rate limit) · Node.js · 최근 푸시 (rate limit) · 카테고리: 🤝 Collaboration & Communication

네이버·다음/카카오·Gmail·네이트·야후·iCloud 6개 메일을 Claude에 연결해 요약·관리하는 MCP 서버입니다.

## 개요

한국에서 주로 쓰는 네이버·다음/카카오 메일을 포함한 6개 메일 서비스(네이버·다음/카카오·Gmail·네이트·Yahoo·iCloud)를 IMAP으로 Claude AI에 연결하는 MCP 서버(v1.4.5). 읽지 않은 메일 수집, 요약·번역, 4단계 스팸 탐지, 통합 인박스 관리를 제공하며, 계정 자격증명은 AES-256-GCM으로 암호화 저장한다. 로컬 설치(Claude Desktop, 인증 없음)와 원격 서버(claude.ai 웹/앱, OAuth 2.0) 두 경로를 지원한다.

## 제공 도구

README 도구 표에 명시된 도구 (총 개수는 README에 단일 표로 열거).

| 도구 | 기능 |
|------|------|
| `check_new_mails` | 읽지 않은 메일 수집, 전체 폴더 순회, 4단계 스팸 탐지 |
| `list_accounts` | 등록된 계정 목록 및 폴더 스캔 현황 |
| `read_email` | 특정 메일 전체 본문 읽기 (`max_chars` 길이 제한) |
| `reset_last_run` | 마지막 실행 시각 초기화 (계정별/날짜 지정) |
| `list_mailboxes` | IMAP 폴더 목록 및 발견/제외/유효 현황 |
| `generate_categories` | 메일 패턴 AI 분석 → 맞춤 카테고리 자동 생성 |
| `get_watched_mailboxes` | 계정별 폴더 스캔 현황 조회 |
| `set_watched_mailboxes` | 스캔 제외 폴더 관리 (추가/제거/초기화) |

## 설치

```bash
git clone https://github.com/youngsooco/k-mail-mcp.git
cd k-mail-mcp
# Windows: install.bat 더블클릭
# macOS/Linux:
chmod +x install.sh && ./install.sh
# 계정 등록: setup.bat (Windows) 또는 ./setup.sh
```

## 필요 키 · 환경변수

| 항목 | 발급처 | 필수 |
|------|--------|------|
| 서비스별 **앱 비밀번호** (IMAP 전용) | 네이버 보안설정 / Google 앱 비밀번호 / 다음 IMAP 설정 등 | ✅ |
| Claude Haiku API 키 (AI 스팸 필터) | [Anthropic](https://console.anthropic.com) | 선택 |

> 로그인 비밀번호가 아닌 앱 비밀번호 필요. 계정 정보는 `setup` 스크립트로 등록되어 AES-256-GCM 암호화 저장.

## 설정 예시

설치 스크립트(`install.bat`/`install.sh`)가 Claude Desktop 설정 파일 연결까지 자동 수행. (README 기반 — 수동 JSON 스니펫은 저장소에 별도 명시 없음)

## 비고

- 네이트 등 일부 서비스는 README에서 "미검증"으로 표기됨.
- 원격 서버 모드는 외부 접근 가능한 서버 + OAuth 2.0 필요.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
