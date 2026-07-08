# korea-statistic-MCP-cginside

> **[jaykim429/korea-statistic-MCP-cginside](https://github.com/jaykim429/korea-statistic-MCP-cginside)** · ⭐ 2 · Python · 최근 푸시 2026-06-29 · 카테고리: 📊 Public Data

KOSIS 국가통계와 NABOSTATS(국회예산정책처) 통계를 자연어로 검색·조회·분석·시각화하는 MCP 서버.

## 개요

KOSIS OpenAPI와 NABOSTATS를 대상으로, "그럴듯하지만 틀린 통계 답변"을 줄이는 데 초점을 둔 MCP 서버다. 최종 답을 지어내지 않고 통계표 선택→코드 매핑→원자료 조회 절차를 응답 표면에 드러낸다. Tier A 직접조회 통계 189개, Tier B 검색 라우팅 219개, 동의어 매핑 90개를 갖춘 `NaturalLanguageRouter`를 내장한다. 권장 흐름은 `plan_query` → `select_table_for_query` → `resolve_concepts` → `query_table` → (필요 시) `compute_indicator`.

## 제공 도구

소스(`kosis_mcp_server.py`)에서 확인된 `@mcp.tool()` 37개:

| 분류 | 도구 |
|------|------|
| 빠른 조회 | `quick_stat`, `quick_trend`, `quick_region_compare`, `daily_term_lookup`, `browse_topic` |
| 분석 | `analyze_trend`, `correlate_stats`, `forecast_stat`, `detect_outliers`, `chain_full_analysis` |
| 차트(SVG) | `chart_line`, `chart_compare_regions`, `chart_correlation`, `chart_heatmap`, `chart_distribution`, `chart_dual_axis`, `chart_dashboard` |
| 질의 계획·검증 | `plan_query`, `answer_query`, `verify_stat_claims`, `stat_time_compare`, `indicator_dependency_map` |
| KOSIS 조회 | `search_kosis`, `search_stats`, `resolve_concepts`, `select_table_for_query`, `curation_status`, `check_stat_availability`, `check_variable_compatibility`, `query_table`, `compute_indicator`, `explore_table`, `decode_error` |
| NABO 조회 | `search_nabo_tables`, `explore_nabo_table`, `query_nabo_table`, `search_nabo_terms` |

## 설치

```bash
python -m pip install "git+https://github.com/jaykim429/korea-statistic-MCP-cginside.git"
# 진입점: kosis-analysis-mcp (stdio) / kosis-analysis-mcp-http (원격 HTTP)
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `KOSIS_API_KEY` | [KOSIS OpenAPI](https://kosis.kr/openapi) | ✅ |
| `NABO_API_KEY` | [NABOSTATS 국회예산정책처](https://www.nabostats.go.kr) | ⛔(NABO 도구 사용 시만) |

## 설정 예시

```json
{
  "mcpServers": {
    "kosis-analysis": {
      "command": "kosis-analysis-mcp",
      "env": { "KOSIS_API_KEY": "YOUR_KOSIS_API_KEY", "NABO_API_KEY": "YOUR_NABO_API_KEY" }
    }
  }
}
```

## 비고

- 로컬 stdio / 원격 HTTP 두 방식 지원(Render/Docker 배포용 `kosis_http_server:main`).
- 라이선스: MIT.

---
*수집일: 2026-07-02 · 출처: 저장소 README, 소스 코드(kosis_mcp_server.py, pyproject.toml)*
