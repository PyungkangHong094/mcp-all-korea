# data-go-mcp-servers

> **[Koomook/data-go-mcp-servers](https://github.com/Koomook/data-go-mcp-servers)** · ⭐ N/A · Python · 최근 푸시 N/A · 카테고리: 📊 Public Data

data.go.kr 공공데이터 API들을 개별 MCP 서버 패키지로 제공하는 모노레포입니다.

## 개요

한국 공공데이터 포털(data.go.kr)의 여러 API를 각각 독립된 PyPI 패키지(`data-go-mcp.*`)로 배포하는 프로젝트. Pydantic 타입 검증을 사용하며 uv/pip으로 개별 설치한다. 현재 6개 서버가 제공된다.

## 제공 서버 · 도구

| 서버 (PyPI 패키지) | 설명 | 확인된 도구 |
|------|------|------|
| `data-go-mcp.nps-business-enrollment` | 국민연금공단 사업장 가입 내역 | `search_business` |
| `data-go-mcp.nts-business-verification` | 국세청 사업자등록 진위확인·상태조회 | `validate_business`, `batch_validate_businesses`, `check_business_status` |
| `data-go-mcp.pps-narajangteo` | 나라장터 입찰공고·낙찰·계약정보 | (README 표에 도구명 미기재) |
| `data-go-mcp.fsc-financial-info` | 금융위원회 기업 재무정보(재무제표·손익) | (README 표에 도구명 미기재) |
| `data-go-mcp.presidential-speeches` | 대통령기록관 연설문 조회 | (README 표에 도구명 미기재) |
| `data-go-mcp.msds-chemical-info` | 물질안전보건자료(MSDS) 화학물질 정보 | (README 표에 도구명 미기재) |

(도구명 출처: README의 NPS·NTS 사용법 섹션. 나머지 4개 서버는 개별 패키지 문서/소스 확인 필요)

## 설치

```bash
# uv (예시)
uv pip install data-go-mcp.nps-business-enrollment
# 또는 pip
pip install data-go-mcp.nts-business-verification
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `API_KEY` | [공공데이터포털](https://www.data.go.kr) | ✅ |

모든 서버가 공통으로 `API_KEY`(data.go.kr 발급 키)를 사용한다.

## 설정 예시

```json
{
  "mcpServers": {
    "nps-business-enrollment": {
      "command": "uvx",
      "args": ["data-go-mcp.nps-business-enrollment"],
      "env": { "API_KEY": "your-api-key-here" }
    }
  }
}
```

## 비고

Apache-2.0 License. 각 서버가 독립 PyPI 패키지이므로 필요한 것만 개별 설치한다. Claude Desktop·Cline 설정 예시 제공. 4개 서버의 도구명은 README 상단 표에 미기재라 개별 패키지 문서/소스에서 확인해야 한다.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
