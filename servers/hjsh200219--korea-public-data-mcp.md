# korea-public-data-mcp

> **[hjsh200219/korea-public-data-mcp](https://github.com/hjsh200219/korea-public-data-mcp)** · ⭐ N/A · TypeScript · 최근 푸시 N/A · 카테고리: 📊 Public Data

국가법령정보센터·DART·공공데이터포털 등 다수의 한국 공공 API를 통합한 대형 MCP 서버입니다.

## 개요

법제처 국가법령정보센터, DART 전자공시, 공공데이터포털, 관세청 UNI-PASS, 수출입은행 환율, 농림축산식품부, 금융감독원 금융상품, 금융위원회 보험, 조달청 나라장터, YouTube, 한국관광공사 KorService2, 쿠팡 파트너스, 국회 Open API, 정부24 plus AI, 해외 판례(CourtListener·OpenLegalData)를 하나로 통합한다. TypeScript + Node, MCP SDK(Streamable HTTP + stdio) 기반. 호스팅 서버(`public-data.up.railway.app`)로 바로 붙거나 셀프 호스팅한다.

## 제공 도구

**법제처 국가법령정보센터 (21개 도구, `LAW_API_OC` 필수):**
`search_laws`/`get_law_detail`, `search_cases`/`get_case_detail`, `search_constitutional`/`get_constitutional_detail`, `search_interpretations`/`get_interpretation_detail`, `search_admin_rules`/`get_admin_rule_detail`, `search_ordinances`/`get_ordinance_detail`, `search_treaties`/`get_treaty_detail`, `search_legal_terms`/`get_legal_term_detail`, `search_english_laws`/`get_english_law_detail`, `search_committee_decisions`/`get_committee_decision_detail`, `search_admin_appeals`/`get_admin_appeal_detail`, `search_old_new_law`/`get_old_new_law_detail`, `search_law_system`/`get_law_system_detail`, `search_three_way_comp`/`get_three_way_comp_detail`, `search_attached_forms`, `search_law_abbreviations`, `search_law_change_history`, `get_law_article_sub`, `search_ai_legal_terms`, `search_linked_ordinances`, `search_admin_rule_old_new`/`get_admin_rule_old_new_detail`

**DART 전자공시 (5개, `DART_API_KEY` 선택):**
`dart_resolve_corp_code`, `dart_search_disclosures`, `dart_get_company_info`, `dart_get_financial_statements`, `dart_get_key_accounts`

**공공데이터포털 (8개, `DATA20_SERVICE_KEY` 선택):**
`data20_search_pharmacy`, `data20_search_hospital`, `data20_search_animal_hospital`, `data20_search_stock_dividend`, `data20_search_rare_medicine`, `data20_search_health_food`, `data20_verify_business`, `data20_check_business_status`

**추가 스킬 계열 (선택):** `tariff_lookup`(관세율·HS코드, `exchange_rate` 액션 포함), `import_clearance`·`export_clearance`(통관), `trade_entity`(무역 업체·수입축산물 이력), `shipping_logistics`(물류), `financial_product`(예적금·대출·펀드), `insurance`(보험 공시, 키 불필요), `procurement`(나라장터 입찰·낙찰, 키 불필요), `youtube`(자막·메타데이터), 한국관광공사 KorService2, 쿠팡 파트너스, 국회 Open API, 정부24 plus AI, 해외 판례(CourtListener·OpenLegalData). (README에 계열/기능은 명시되나 일부 하위 도구명은 소스 확인 필요)

## 설치

```bash
# 셀프 호스팅
git clone https://github.com/hjsh200219/public-data-mcp.git
cd public-data-mcp
npm install
npm run build
npm start
```

호스팅 서버 사용 시 설치 불필요 — `https://public-data.up.railway.app/mcp` URL로 연결.

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `LAW_API_OC` | [법제처 오픈API](https://open.law.go.kr/LSO/openApi/guideList.do) | ✅ |
| `DART_API_KEY` | [DART 오픈API](https://opendart.fss.or.kr) | ⬜ |
| `DATA20_SERVICE_KEY` | [공공데이터포털](https://www.data.go.kr) | ⬜ |
| `UNIPASS_KEY_API*` | 관세청 UNI-PASS (API 번호별 개별 키) | ⬜ |
| `EXCHANGE_RATE_API_KEY` | 수출입은행 환율 | ⬜ |
| `MAFRA_API_KEY` | 농림축산식품부 | ⬜ |
| `FINLIFE_API_KEY` | 금융감독원 금융상품 비교공시 | ⬜ |
| `YOUTUBE_API_KEY` | YouTube Data API v3 | ⬜ |
| `COUPANG_ACCESS_KEY` / `COUPANG_SECRET_KEY` | 쿠팡 파트너스 | ⬜ |
| `ASSEMBLY_API_KEY` | [국회 Open API](https://open.assembly.go.kr) | ⬜ |
| `COURTLISTENER_API_TOKEN` / `OPENLEGALDATA_API_TOKEN` | 해외 판례(미국/독일) | ⬜ |

`LAW_API_OC`만 필수, 나머지는 해당 기능 사용 시 선택.

## 설정 예시

```json
{
  "mcpServers": {
    "korea-public-data": {
      "url": "https://public-data.up.railway.app/mcp"
    }
  }
}
```

## 비고

REST API(`/api/search/{type}`, `/api/detail/{type}/{id}`, `/openapi.json`)도 제공. 셀프 호스팅 저장소는 `hjsh200219/public-data-mcp`. 스킬 계열 도구의 세부 하위 도구명은 소스 확인 필요.

---
*수집일: 2026-07-02 · 출처: 저장소 README*
