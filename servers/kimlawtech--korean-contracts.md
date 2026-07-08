# korean-contracts

> **[kimlawtech/korean-contracts](https://github.com/kimlawtech/korean-contracts)** · ⭐ 47 · Go Template · 최근 푸시 2026-04-22 · 카테고리: 📜 Legal & Government

한국 사업자용 계약서 9종 자동 생성 Claude Code 스킬 + 개인정보 마스킹 MCP 보안 서버.

## 개요

창업자·HR·소상공인이 근로·알바·유연근무·일용·프리랜서·외주용역·연봉 등 9종 계약서를 Claude Code에서 대화형으로 작성하는 스킬 모음이다. 2026년 최저임금(10,320원/시)·최신 대법원 판례를 반영하고 RULE 1~14 법률 검증을 거쳐 `.txt` + `.docx`로 생성한다. 핵심은 v2.1에서 추가된 **MCP 보안 서버**로, 계약서에 들어가는 이름·주민번호·주소·급여 등 민감 개인정보를 로컬에서 토큰으로 마스킹한 뒤 Claude에 전달하고, 최종 저장 시 원본으로 복원한다.

## 제공 도구

MCP 보안 서버가 노출하는 도구 5종(개인정보 로컬 마스킹용):

| 도구 | 기능 |
|------|------|
| `mask_personal_info` | 변수 맵을 받아 개인정보를 토큰화, 세션 메모리에 원본 저장 |
| `save_contract` | 마스킹된 계약서 텍스트를 복원해 `.txt` + `.docx` 저장 |
| `load_contract_for_review` | 기존 계약서 파일 읽기 + 자동 마스킹 |
| `save_reviewed_contract` | 검토 후 수정된 계약서 복원 저장 |
| `list_sessions` | 활성 세션 목록 조회 (디버깅용) |

개인정보는 `PERSON_A`/`PERSON_B`/`ID_FRONT`/`ADDRESS_A`/`CONTACT_A`/`BIZ_NO` 등의 토큰으로 치환되어 로컬 세션 메모리에만 원본이 저장된다. 계약서 작성 자체는 `/employment-contract` 등 Claude Code 스킬(슬래시 명령)로 수행한다.

## 설치

```
# Claude Code 스킬 + 로컬 MCP 서버 구성 (저장소 참조)
# 스킬: /korean-contracts, /employment-contract 등 슬래시 명령
```

(README에 표준 `claude_desktop_config.json` 스니펫은 명시되지 않음 — 로컬 MCP 서버로 구동)

## 필요 키 · 환경변수

**API 키 불필요** — 개인정보 마스킹은 전적으로 로컬 세션 메모리에서 처리된다.

## 설정 예시

README에 표준 `claude_desktop_config.json` 스니펫은 제공되지 않는다. 순수 MCP 서버가 아니라 Claude Code 스킬 + 로컬 MCP 보안 서버 결합 프로젝트로, 로컬 MCP 서버로 구동하며 설치·구성은 저장소 안내(슬래시 명령 `/korean-contracts` 등)를 따른다.

## 비고

- 라이선스: Apache 2.0(README 배지 기준. GitHub 메타는 Other로 표기). 버전 2.1.0.
- 순수 MCP 서버가 아니라 **Claude Code 스킬 + MCP 보안 서버 결합 프로젝트**다. 계약서 생성 로직은 스킬, 개인정보 보호는 MCP가 담당.
- 한국 법률 AI 허브 SpeciAI에서 개발.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
