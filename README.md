# Awesome MCP Korea (mcp-all-korea)

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Servers](https://img.shields.io/badge/servers-156-blue)
![Categories](https://img.shields.io/badge/categories-12-brightgreen)
![License](https://img.shields.io/badge/license-CC0--1.0-lightgrey)

한국 생태계를 위해 구축된 MCP(Model Context Protocol) 서버 및 도구를 선별한 목록입니다.
법률, 커머스, 공공데이터, 금융, **부동산**, **지도·지역**, 관광, 날씨, 한국어 NLP 등 한국 특화 서비스를 폭넓게 다룹니다.
커뮤니티 기반으로 유지되며, 누구나 기여할 수 있습니다.

A curated list of MCP (Model Context Protocol) servers and tools built for the Korean market and ecosystem.
Covers legal systems, commerce, public data, finance, **real estate**, **maps & regional data**, tourism, weather, Korean NLP, and other Korea-specific integrations.
Community-driven and open to contributions.

> ⚠️ **보안 면책 고지 (Security Disclaimer)**
>
> 이 저장소는 MCP 서버 및 도구를 **목록화하는 것만을 목적**으로 합니다.
> 등재된 프로젝트의 보안, 안전성, 신뢰성에 대해 이 저장소는 어떠한 책임도 지지 않습니다.
> 각 도구의 사용에 따른 보안 위험은 **사용자 본인이 직접 검토하고 책임져야 합니다.**
>
> This repository exists solely for **listing purposes**.
> We make no guarantees regarding the security, safety, or reliability of any listed project.
> **Each user is solely responsible** for evaluating and assuming any security risks associated with the tools they choose to use.

---

## 📑 목차 (Table of Contents)

- [MCP란 무엇인가?](#mcp란-무엇인가)
- [빠른 활용 시나리오 (Recommended Stacks)](#-빠른-활용-시나리오-recommended-stacks)
- [선정 기준 (Inclusion Criteria)](#선정-기준-inclusion-criteria)
- **목록 (List)**
  - [📜 Legal & Government](#-legal--government) · 법률·정부 (15)
  - [🛒 Commerce & Retail](#-commerce--retail) · 커머스 (4)
  - [🏦 Finance & Tax](#-finance--tax) · 금융·세금 (32)
  - [🏠 Real Estate](#-real-estate) · 부동산 (12)
  - [🗺 Maps & Address](#-maps--address) · 지도·주소 (11)
  - [🔎 Search & Trends](#-search--trends) · 검색·트렌드 (19)
  - [🌏 Tourism & Travel](#-tourism--travel) · 관광·여행 (4)
  - [📊 Public Data](#-public-data) · 공공데이터·지역 (23)
  - [🌦 Weather](#-weather) · 날씨 (7)
  - [🔤 Korean NLP & Language](#-korean-nlp--language) · 한국어 (12)
  - [🤝 Collaboration & Communication](#-collaboration--communication) · 협업 (8)
  - [🧩 Miscellaneous](#-miscellaneous) · 기타 (9)
- [기여 방법 (Contributing)](#기여-방법-contributing)
- [라이선스 (License)](#라이선스-license)

---

## MCP란 무엇인가?

MCP(Model Context Protocol)는 AI 모델이 외부 도구, 데이터 소스, 서비스와 표준화된 방식으로 상호작용할 수 있도록 설계된 개방형 프로토콜입니다.
이 목록은 그 중에서도 한국 생태계에 특화된 구현체를 모아 제공합니다.

MCP (Model Context Protocol) is an open protocol that enables AI models to interact with external tools, data sources, and services in a standardized way.
This list focuses on implementations specifically tailored to the Korean ecosystem.

---

## 🧭 빠른 활용 시나리오 (Recommended Stacks)

여러 MCP 서버를 조합하면 단일 서버로는 어려운 분석이 가능합니다. 특히 **부동산·지역 분석**은 아래처럼 여러 소스를 엮을 때 인사이트가 극대화됩니다.

| 목적 | 조합 (Stack) | 흐름 |
|------|-------------|------|
| **부동산 투자 분석** | Real Estate + Maps + Public Data + Finance | 주소 → 실거래가 조회 → 지도·주변환경 확인 → 지역 통계·금리로 시세 해석 |
| **지역(입지) 분석** | Maps & Address + Public Data + Tourism | 법정동·좌표 변환 → 인구·교통·상권 통계 → 주변 관광·생활 인프라 |
| **정책·규제 확인** | Legal & Government + Public Data | 법령·판례 검색 → 관련 공공데이터·통계로 근거 보강 |
| **기업·투자 리서치** | Finance & Tax + Legal & Government | DART 공시·재무 → 관련 법령·규제 교차 확인 |

> 💡 **부동산 실무 워크플로우 예시**
> 1. **주소 → 법정동코드** 변환 (Maps/Address 또는 행정구역 계열)
> 2. **실거래가** 조회 (Real Estate — 국토부 RTMS)
> 3. **지역 통계·지수** 확인 (Public Data — KOSIS / 부동산원)
> 4. **위치·주변환경** 시각화 (Maps — 네이버/카카오 지도)
> 5. **금리·거시지표** 로 시세 맥락 해석 (Finance)

---

## 선정 기준 (Inclusion Criteria)

아래 기준을 모두 충족하는 프로젝트만 등재합니다.

- 공개적으로 접근 가능한 저장소여야 합니다.
- 한국 생태계를 명확하게 지원해야 합니다.
- MCP 명세를 구현해야 합니다.
- 기본적인 문서가 포함되어야 합니다.
- 마케팅 목적만의 저장소는 허용하지 않습니다.

Only projects meeting all of the following criteria are listed.

- Must be publicly accessible.
- Must clearly support the Korean ecosystem.
- Must implement the MCP specification.
- Must include basic documentation.
- Marketing-only repositories are not accepted.

---

## 목록 (List)

### 📜 Legal & Government

> 한국 법률, 판례, 정부 공공 서비스 관련 MCP 서버 · MCP servers for Korean law, court rulings, and government services.

**[chrisryugj/korean-law-mcp](https://github.com/chrisryugj/korean-law-mcp)** – 국가법령정보 Open API를 기반으로 법령·판례·행정규칙 등을 검색·조회·분석하는 MCP 서버입니다. · [📄 상세](servers/chrisryugj--korean-law-mcp.md)

**[ChangooLee/mcp-kr-legislation](https://github.com/ChangooLee/mcp-kr-legislation)** – 법제처 OPEN API를 통합해 법령·판례·행정규칙·자치법규·조약·별표서식 등 한국 법률 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/ChangooLee--mcp-kr-legislation.md)

**[hollobit/assembly-api-mcp](https://github.com/hollobit/assembly-api-mcp)** – 대한민국 국회 Open API와 국민참여입법센터·NABO API를 연동해 국회의원·의안·일정·회의록·청원·예산정책처 자료를 조회하는 MCP 서버입니다. · [📄 상세](servers/hollobit--assembly-api-mcp.md)

**[finalchild/law-mcp](https://github.com/finalchild/law-mcp)** – open.law.go.kr API를 통해 한국 법령 데이터를 조회하는 MCP 서버입니다. · [📄 상세](servers/finalchild--law-mcp.md)

**[DrMoony/koregx](https://github.com/DrMoony/koregx)** – 한국 헬스케어 법령, 행정해석, 식약처·복지부 행정규칙, HIRA 결정을 통합 조회하는 웹 서비스 및 MCP 서버입니다. · [📄 상세](servers/DrMoony--koregx.md)

**[seung23/lawtutor-mcp](https://github.com/seung23/lawtutor-mcp)** – 국가법령정보센터 데이터를 기반으로 7급 공무원시험 행정법·헌법 학습용 RAG 검색 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/seung23--lawtutor-mcp.md)

**[rabqatab/LexLink-ko-mcp](https://github.com/rabqatab/LexLink-ko-mcp)** – 국가법령정보센터 Open API 기반으로 법령·판례·행정규칙·헌재결정례·행정심판례를 구조적으로 제공하고 시맨틱 검색(aiSearch)을 지원하는 MCP 서버입니다. · [📄 상세](servers/rabqatab--LexLink-ko-mcp.md)

**[SeoNaRu/korean-law-mcp](https://github.com/SeoNaRu/korean-law-mcp)** – 국가법령정보센터 Open API로 한국 법령·판례·행정규칙 검색을 제공하는 MCP 서버입니다. · [📄 상세](servers/SeoNaRu--korean-law-mcp.md)

**[workbookbulb863/korean-law-alio-mcp](https://github.com/workbookbulb863/korean-law-alio-mcp)** – 국가법령정보센터와 ALIO 공공기관 내부규정을 함께 검색·비교·분석하는 MCP 서버입니다.

**[kimlawtech/korean-contracts](https://github.com/kimlawtech/korean-contracts)** – 근로·프리랜서·용역 등 9종 한국 계약서를 자동 생성하고, 개인정보 마스킹 MCP 서버로 민감정보를 로컬에서 보호하는 프로젝트입니다. · [📄 상세](servers/kimlawtech--korean-contracts.md)

**[seunghan91/korea-law-mcp-public](https://github.com/seunghan91/korea-law-mcp-public)** – 법제처 Open API와 하이브리드 검색(BM25+벡터)으로 국가법령·자치법규·판례를 조문 단위로 인용 조회하는 MCP 서버입니다. · [📄 상세](servers/seunghan91--korea-law-mcp-public.md)

**[smilemin07/korean-rnd-regs-mcp](https://github.com/smilemin07/korean-rnd-regs-mcp)** – 국가법령정보센터 API로 국가 R&D 관련 규정 49종을 검색·검토하는 MCP 서버입니다. · [📄 상세](servers/smilemin07--korean-rnd-regs-mcp.md)

**[shinkeonkim/e-gonghun-mcp](https://github.com/shinkeonkim/e-gonghun-mcp)** – 독립유공자 공적조서·포상 기록을 조회하는 e-공훈 MCP 서버입니다. · [📄 상세](servers/shinkeonkim--e-gonghun-mcp.md)

**[seo-jinseok/korean-law-mcp](https://github.com/seo-jinseok/korean-law-mcp)** – 법제처 Open API로 법령·판례·행정규칙·법령해석례·서식을 검색하는 MCP 서버입니다. · [📄 상세](servers/seo-jinseok--korean-law-mcp.md)

**[legalize-kr/cli-tools](https://github.com/legalize-kr/cli-tools)** – GitHub REST API로 미러링된 한국 법령·판례·행정규칙·자치법규를 클론·인증 없이 조회하는 CLI 겸 로컬 stdio MCP 서버(legalize-mcp)입니다. · [📄 상세](servers/legalize-kr--cli-tools.md)

---

### 🛒 Commerce & Retail

> 한국 전자상거래, 오픈마켓, 쇼핑 서비스 관련 MCP 서버 · MCP servers for Korean e-commerce, open markets, and shopping.

**[hmmhmmhm/daiso-mcp](https://github.com/hmmhmmhm/daiso-mcp)** – 주변 다이소 매장을 검색하고 원하는 상품의 재고 여부 및 가격을 조회하는 MCP 서버입니다. · [📄 상세](servers/hmmhmmhm--daiso-mcp.md)

**[edward-kim-dev/kr-pc-deals-mcp](https://github.com/edward-kim-dev/kr-pc-deals-mcp)** – 다나와·컴퓨존 PC 부품 최저가 검색, 가격 비교, 가격 이력, 빌드 견적, CPU-메인보드-RAM 호환성 체크를 제공하는 MCP 서버입니다. · [📄 상세](servers/edward-kim-dev--kr-pc-deals-mcp.md)

**[pak3430/Reservation-Platform-MCP-Server](https://github.com/pak3430/Reservation-Platform-MCP-Server)** – 네이버·에어비앤비·스페이스클라우드·야놀자·카카오 예약을 iCal 표준으로 통합 관리하는 MCP 서버입니다. · [📄 상세](servers/pak3430--Reservation-Platform-MCP-Server.md)

**[uju777/coupang-mcp](https://github.com/uju777/coupang-mcp)** – 쿠팡 상품 검색과 다나와 실시간 최저가 비교(로켓배송·중고 포함)를 제공하는 MCP 서버입니다 (쿠팡 API 키 필요). · [📄 상세](servers/uju777--coupang-mcp.md)

---

### 🏦 Finance & Tax

> 한국 금융, 세금, 주식, 암호화폐 관련 MCP 서버 · MCP servers for Korean finance, tax, stocks, and crypto.

**[migusdn/KIS_MCP_Server](https://github.com/migusdn/KIS_MCP_Server)** – 한국투자증권(KIS) REST API를 통해 국내·해외 주식 시세 조회와 주문 기능을 제공하는 MCP 서버입니다. · [📄 상세](servers/migusdn--KIS_MCP_Server.md)

**[Mrbaeksang/korea-stock-analyzer-mcp](https://github.com/Mrbaeksang/korea-stock-analyzer-mcp)** – 한국 주식의 재무·기술지표·DCF·뉴스·수급을 통합 분석하는 MCP 서버입니다. · [📄 상세](servers/Mrbaeksang--korea-stock-analyzer-mcp.md)

**[jjlabsio/korea-stock-mcp](https://github.com/jjlabsio/korea-stock-mcp)** – DART와 KRX 공식 API를 연동해 공시·재무제표·주가 데이터를 조회하는 한국 주식 분석 MCP 서버입니다. · [📄 상세](servers/jjlabsio--korea-stock-mcp.md)

**[aesthetic-legalism5470/korean-dart-mcp](https://github.com/aesthetic-legalism5470/korean-dart-mcp)** – OpenDART API를 기반으로 공시·재무·지분·XBRL 데이터를 조회하고 첨부 문서를 처리하는 MCP 서버입니다. · [📄 상세](servers/aesthetic-legalism5470--korean-dart-mcp.md)

**[koreainvestment/koreainvestment-mcp](https://github.com/koreainvestment/koreainvestment-mcp)** – 한국투자증권 API를 자연어로 검색해 필요한 금융 API를 찾을 수 있는 MCP 서버입니다. · [📄 상세](servers/koreainvestment--koreainvestment-mcp.md)

**[sharebook-kr/pykrx-mcp](https://github.com/sharebook-kr/pykrx-mcp)** – pykrx 라이브러리 기반으로 KOSPI·KOSDAQ·KONEX 주가, 재무제표, 투자자별 수급 및 공매도 데이터를 제공하는 MCP 서버입니다. · [📄 상세](servers/sharebook-kr--pykrx-mcp.md)

**[redoxnet/mcp-lsopenapi](https://github.com/redoxnet/mcp-lsopenapi)** – LS증권 OpenAPI를 통해 국내 주식 시세, 차트, 지표 데이터를 자연어 도구로 조회하는 MCP 서버입니다. · [📄 상세](servers/redoxnet--mcp-lsopenapi.md)

**[snaiws/DART-mcp-server](https://github.com/snaiws/DART-mcp-server)** – 금융감독원 DART API를 활용해 상장기업 공시, 기업 개황, 재무 정보 등을 조회하는 MCP 서버입니다. · [📄 상세](servers/snaiws--DART-mcp-server.md)

**[java-jaydev/kiwoom-mcp](https://github.com/java-jaydev/kiwoom-mcp)** – 키움증권 REST API로 국내 주식 현재가·호가·일봉·투자자 동향·계좌 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/java-jaydev--kiwoom-mcp.md)

**[MarcoYou/open-proxy-mcp](https://github.com/MarcoYou/open-proxy-mcp)** – DART 전자공시(주주총회 안건 등)를 지분구조·재무지표·리스크 이벤트로 구조화해 분석하는 MCP 서버입니다. · [📄 상세](servers/MarcoYou--open-proxy-mcp.md)

**[chrisryugj/korean-dart-mcp](https://github.com/chrisryugj/korean-dart-mcp)** – OpenDART 83개 API를 15개 도구로 묶고 내부자 시그널·회계 리스크·HWP/PDF 첨부 변환까지 제공하는 MCP 서버입니다. · [📄 상세](servers/chrisryugj--korean-dart-mcp.md)

**[whdrnr2583-cmd/koreanpulse](https://github.com/whdrnr2583-cmd/koreanpulse)** – 한국 DART 공시·5%룰 외국인 지분 흐름·행동주의 공시를 영어로 번역·제공하는 한국 주식 인텔리전스 MCP 서버입니다. · [📄 상세](servers/whdrnr2583-cmd--koreanpulse.md)

**[RealYoungk/opendart-mcp](https://github.com/RealYoungk/opendart-mcp)** – 금감원 DART 전자공시 Open API 83종을 자연어로 조회하는 MCP 서버입니다. · [📄 상세](servers/RealYoungk--opendart-mcp.md)

**[openpharma-org/asia-filings-mcp-server](https://github.com/openpharma-org/asia-filings-mcp-server)** – 일본 EDINET과 한국 DART로 아시아 7,700개 기업 재무공시를 검색·분석하는 MCP 서버입니다(한·일 다국가). · [📄 상세](servers/openpharma-org--asia-filings-mcp-server.md)

**[keonho-kim/OpenDart-mcp](https://github.com/keonho-kim/OpenDart-mcp)** – DART API를 MCP로 제공해 기업 기본정보·금융정보 조회·분석을 지원하는 파이썬 MCP 서버입니다. · [📄 상세](servers/keonho-kim--OpenDart-mcp.md)

**[BrainDAO/mcp-upbit](https://github.com/BrainDAO/mcp-upbit)** – 업비트 거래소의 공개 시세 조회와 선택적 사설 거래 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/BrainDAO--mcp-upbit.md)

**[scjang01/tossinvest-mcp](https://github.com/scjang01/tossinvest-mcp)** – 토스증권 Open API로 현재가·호가·캔들·잔고·주문을 조회하는 한국 주식 MCP 서버입니다. · [📄 상세](servers/scjang01--tossinvest-mcp.md)

**[kwonsw812/kiwoom-mcp](https://github.com/kwonsw812/kiwoom-mcp)** – 키움증권 계좌를 자연어로 제어해 주가 조회·매매 주문을 수행하는 MCP 서버입니다. · [📄 상세](servers/kwonsw812--kiwoom-mcp.md)

**[hypn4/opendart-fss-mcp](https://github.com/hypn4/opendart-fss-mcp)** – 금융감독원 DART API를 85개 도구로 재무제표·정기보고서·지분공시를 조회하는 MCP 서버입니다. · [📄 상세](servers/hypn4--opendart-fss-mcp.md)

**[ctk03272/mcp-korean-stock](https://github.com/ctk03272/mcp-korean-stock)** – FinanceDataReader와 네이버 차트 API로 한국 주식 종목·일봉·10분봉과 기술지표를 제공하는 MCP 서버입니다. · [📄 상세](servers/ctk03272--mcp-korean-stock.md)

**[Kerydos/kiwoom_api_MCP](https://github.com/Kerydos/kiwoom_api_MCP)** – 키움 REST API 문서를 검색·조회하고 요청 예제 코드를 생성하는 MCP 서버입니다. · [📄 상세](servers/Kerydos--kiwoom_api_MCP.md)

**[2geonhyup/dart-mcp-test](https://github.com/2geonhyup/dart-mcp-test)** – DART API로 상장기업 재무 데이터를 분석·시각화하는 Claude 확장 MCP 서버입니다. · [📄 상세](servers/2geonhyup--dart-mcp-test.md)

**[vertical-mcp/dart-mcp](https://github.com/vertical-mcp/dart-mcp)** – 금감원 DART 전자공시(OpenDART) API로 기업 공시·개황·재무제표를 조회하는 MCP 서버입니다. · [📄 상세](servers/vertical-mcp--dart-mcp.md)

**[nss133/dart-mcp](https://github.com/nss133/dart-mcp)** – OPEN DART(금감원 전자공시) 1차 공시 원본·지분공시·재무제표를 법무 검토용으로 제공하는 MCP 서버입니다. · [📄 상세](servers/nss133--dart-mcp.md)

**[junter1989k-ai/korea-payments-mcp](https://github.com/junter1989k-ai/korea-payments-mcp)** – 토스페이먼츠 결제창으로 카드·카카오페이·네이버페이·가상계좌 등 한국 결제를 처리하는 MCP 서버입니다. · [📄 상세](servers/junter1989k-ai--korea-payments-mcp.md)

**[zereight/bithumb-mcp](https://github.com/zereight/bithumb-mcp)** – 빗썸(Bithumb) 거래소 API로 시세·호가·캔들·잔고 조회 및 주문·출금을 처리하는 18개 도구 MCP 서버입니다. · [📄 상세](servers/zereight--bithumb-mcp.md)

**[kokogo100/ragalgo-mcp-server](https://github.com/kokogo100/ragalgo-mcp-server)** – KOSPI/KOSDAQ·Upbit 대상 점수화된 뉴스 감성·기술적 분석·재무·스냅샷을 제공하는 RAG 기반 한국 금융 MCP 서버입니다. · [📄 상세](servers/kokogo100--ragalgo-mcp-server.md)

**[bakyang2/kr-crypto-intelligence](https://github.com/bakyang2/kr-crypto-intelligence)** – 180+ 토큰 김치프리미엄·Upbit/Bithumb 시세·한국어 감성분석을 제공하는 크립토 인텔리전스 MCP 서버입니다. · [📄 상세](servers/bakyang2--kr-crypto-intelligence.md)

**[navyjeongs/stock-news-mcp](https://github.com/navyjeongs/stock-news-mcp)** – 주식 뉴스·종목 분석·포트폴리오 관리를 제공하며 국내 뉴스를 네이버 검색 API로 가져오는 MCP 서버입니다. · [📄 상세](servers/navyjeongs--stock-news-mcp.md)

**[solangii/upbit-mcp-server](https://github.com/solangii/upbit-mcp-server)** – 업비트(Upbit) 거래소 OpenAPI로 시세·계좌·주문·입출금·기술분석을 제공하는 MCP 서버입니다. · [📄 상세](servers/solangii--upbit-mcp-server.md)

**[restful3/upbit-mcp-sse](https://github.com/restful3/upbit-mcp-sse)** – 업비트 OpenAPI를 SSE(Server-Sent Events)로 제공해 n8n 연동을 지원하는 MCP 서버입니다(solangii/upbit-mcp-server 기반). · [📄 상세](servers/restful3--upbit-mcp-sse.md)

**[nangchang/stock-toss-mcp](https://github.com/nangchang/stock-toss-mcp)** – 토스증권 Open API로 주식 거래·시장 데이터·계좌 관리를 연동하는 MCP 서버입니다. · [📄 상세](servers/nangchang--stock-toss-mcp.md)

---

### 🏠 Real Estate

> 한국 부동산 실거래가, 등기, 청약, 투자분석 관련 MCP 서버 · MCP servers for Korean real estate, transactions, and housing subscriptions.

**[ChangooLee/mcp-kr-realestate](https://github.com/ChangooLee/mcp-kr-realestate)** – 국토부 실거래가와 ECOS 등 공공 API를 통합해 한국 부동산 투자 분석을 수행하는 MCP 서버입니다.

**[choihyeokbin/kakao-real-estate-mcp](https://github.com/choihyeokbin/kakao-real-estate-mcp)** – 국토교통부 공공 API와 카카오맵 API를 활용해 실거래가 기반 매물 검색·시세 조회·중간지점 추천을 제공하는 MCP 서버입니다. · [📄 상세](servers/choihyeokbin--kakao-real-estate-mcp.md)

**[gum798/A2A-MCP-RealEstate](https://github.com/gum798/A2A-MCP-RealEstate)** – 국토부 실거래가와 위치 데이터를 바탕으로 투자가치·삶의질을 종합 평가하는 한국 부동산 추천 MCP 서버입니다. · [📄 상세](servers/gum798--A2A-MCP-RealEstate.md)

**[hjongc/lease-safe-mcp](https://github.com/hjongc/lease-safe-mcp)** – 공공 부동산 데이터와 정부 지침을 기반으로 전월세 안전도 평가, 법정동코드 변환, 시장 비교 등 10가지 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/hjongc--lease-safe-mcp.md)

**[immortal0900/Real-Estate-Location-Analyzer_MCP](https://github.com/immortal0900/Real-Estate-Location-Analyzer_MCP)** – 카카오 로컬 API로 주소 반경 내 교육·교통·편의·자연환경·미래가치 등 부동산 입지 요소를 분석하는 MCP 서버입니다. · [📄 상세](servers/immortal0900--Real-Estate-Location-Analyzer_MCP.md)

**[kimduksoo/naver-land-mcp](https://github.com/kimduksoo/naver-land-mcp)** – 네이버 부동산 비공식 API로 지역·좌표 기반 매물 조회, 단지 정보, 시세 추이를 제공하는 MCP 서버입니다. · [📄 상세](servers/kimduksoo--naver-land-mcp.md)

**[ngwoon/korea-realestate-mcp](https://github.com/ngwoon/korea-realestate-mcp)** – 네이버 부동산·직방·다방 등 여러 부동산 플랫폼의 매물 정보를 통합 조회하는 MCP 서버입니다. · [📄 상세](servers/ngwoon--korea-realestate-mcp.md)

**[ohkyuetaek/korea-realestate-mcp](https://github.com/ohkyuetaek/korea-realestate-mcp)** – 공공데이터포털 국토교통부 API로 아파트 매매·전월세 시세 조회, 가격 추이 분석, 지역 비교 등 8가지 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/ohkyuetaek--korea-realestate-mcp.md)

**[Seonh0/naver-land-mcp](https://github.com/Seonh0/naver-land-mcp)** – 네이버 부동산 비공식 API로 전국 아파트 매물·시세·실거래가를 조회하는 6개 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/Seonh0--naver-land-mcp.md)

**[tae0y/real-estate-mcp](https://github.com/tae0y/real-estate-mcp)** – 국토교통부·온비드·청약홈 데이터를 기반으로 한국 부동산 매매·전월세·청약 정보를 제공하는 MCP 서버입니다. · [📄 상세](servers/tae0y--real-estate-mcp.md)

**[coding-realtor/building-register-mcp](https://github.com/coding-realtor/building-register-mcp)** – data.go.kr 건축물대장 API로 표제부·층별·공시가격 등 12개 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/coding-realtor--building-register-mcp.md)

**[hyunsuleedev/naverestate-mcp](https://github.com/hyunsuleedev/naverestate-mcp)** – Playwright로 네이버 부동산 아파트 매물 데이터를 수집하는 MCP 서버입니다. · [📄 상세](servers/hyunsuleedev--naverestate-mcp.md)

---

### 🗺 Maps & Address

> 한국 지도, 주소, 좌표, 길찾기, 지역 위치 서비스 관련 MCP 서버 · MCP servers for Korean maps, addresses, geocoding, and routing.

**[flor3z-github/navermap-mcp-server](https://github.com/flor3z-github/navermap-mcp-server)** – 네이버 클라우드 Maps API를 통해 주소·좌표 변환(지오코딩/역지오코딩), 경로 탐색, 정적 지도 이미지 생성, API 사용량 조회 기능을 제공하는 MCP 서버입니다. · [📄 상세](servers/flor3z-github--navermap-mcp-server.md)

**[yeonupark/mcp-naver-map](https://github.com/yeonupark/mcp-naver-map)** – NCP Geolocation API와 Directions15 API를 연동해 IP 기반 위치 조회 및 드라이빙 경로 탐색을 제공하는 MCP 서버입니다. · [📄 상세](servers/yeonupark--mcp-naver-map.md)

**[yunkee-lee/mcp-naver-maps](https://github.com/yunkee-lee/mcp-naver-maps)** – 네이버 지도 API(지오코딩)와 네이버 검색 API(로컬 검색)를 연동하는 MCP 서버입니다. · [📄 상세](servers/yunkee-lee--mcp-naver-maps.md)

**[CaChiJ/kakao-navigation-mcp-server](https://github.com/CaChiJ/kakao-navigation-mcp-server)** – 카카오 모빌리티 및 카카오맵 API를 연동해 위치 검색(지오코딩)과 도보·자동차 길찾기 서비스를 제공하는 MCP 서버입니다. · [📄 상세](servers/CaChiJ--kakao-navigation-mcp-server.md)

**[jeong-sik/kakao-api-mcp-server](https://github.com/jeong-sik/kakao-api-mcp-server)** – 카카오맵 API와 Daum 검색 API를 연동해 장소 검색, 좌표-주소 변환, 길찾기, 웹·이미지·블로그·카페 검색을 제공하는 MCP 서버입니다. · [📄 상세](servers/jeong-sik--kakao-api-mcp-server.md)

**[cgoinglove/mcp-server-kakao-map](https://github.com/cgoinglove/mcp-server-kakao-map)** – 카카오맵 API 키워드 검색을 통해 한국 내 식당·카페·관광명소 등 장소를 추천하는 MCP 서버입니다. · [📄 상세](servers/cgoinglove--mcp-server-kakao-map.md)

**[heznpc/cairn](https://github.com/heznpc/cairn)** – 주소를 입력하면 한국식 약도(pictogram map) SVG를 자동 생성하고 지오코딩·주변 랜드마크·도로를 조회하는 MCP 서버입니다. · [📄 상세](servers/heznpc--cairn.md)

**[zeikar/kimcp](https://github.com/zeikar/kimcp)** – 네이버 블로그·뉴스 검색과 카카오맵 장소 검색·자동차·대중교통 길찾기 등 국내 주요 플랫폼 기능을 제공하는 MCP 서버입니다. · [📄 상세](servers/zeikar--kimcp.md)

**[jeon3709-dev/vworld-mcp](https://github.com/jeon3709-dev/vworld-mcp)** – VWorld Open API로 필지 경계·지적정보·용도지역·공시지가를 조회하는 부동산 개발용 MCP 서버입니다. · [📄 상세](servers/jeon3709-dev--vworld-mcp.md)

**[yunkee-lee/mcp-kakao-local](https://github.com/yunkee-lee/mcp-kakao-local)** – 카카오 로컬 API 및 카카오맵에 연결해 주소 지오코딩·장소 검색·위치 상세정보를 제공하는 MCP 서버입니다. · [📄 상세](servers/yunkee-lee--mcp-kakao-local.md)

**[Leejinhoe/kakao_mcp_secretary](https://github.com/Leejinhoe/kakao_mcp_secretary)** – 카카오 로컬·모빌리티·톡캘린더·메시지 API로 일정 중복과 이동 불가 동선을 감지하고 경로를 최적화하는 생활동선 보조 MCP 서버입니다. · [📄 상세](servers/Leejinhoe--kakao_mcp_secretary.md)

---

### 🔎 Search & Trends

> 한국 검색 포털 및 트렌드 데이터 분석 관련 MCP 서버 · MCP servers for Korean search portals and trend analysis.

**[isnow890/naver-search-mcp](https://github.com/isnow890/naver-search-mcp)** – 네이버 검색 API와 데이터랩 API를 연동해 한국 서비스 특화 검색·트렌드 분석을 제공하는 MCP 서버입니다. · [📄 상세](servers/isnow890--naver-search-mcp.md)

**[jikime/py-mcp-naver-search](https://github.com/jikime/py-mcp-naver-search)** – 네이버 검색 API로 다양한 콘텐츠 검색 결과를 LLM이 처리하기 쉬운 구조화된 텍스트로 제공하는 MCP 서버입니다. · [📄 상세](servers/jikime--py-mcp-naver-search.md)

**[dataartai/naver-api-mcp](https://github.com/dataartai/naver-api-mcp)** – 네이버 쇼핑인사이트·검색 API로 카테고리·키워드 트렌드와 블로그·지식iN·쇼핑 검색을 제공하는 MCP 서버입니다. · [📄 상세](servers/dataartai--naver-api-mcp.md)

**[uju777/mcp-server-naver-search](https://github.com/uju777/mcp-server-naver-search)** – 네이버 쇼핑·카페·뉴스·블로그 검색 API를 연동해 최저가 비교, 실사용자 후기, 실시간 뉴스를 조회하는 MCP 서버입니다. · [📄 상세](servers/uju777--mcp-server-naver-search.md)

**[insung8150/AgentWebSearch-MCP](https://github.com/insung8150/AgentWebSearch-MCP)** – API 키 없이 Chrome 브라우저(CDP)로 네이버·구글·Brave를 병렬 검색하는 로컬 웹서치 MCP 서버입니다. · [📄 상세](servers/insung8150--AgentWebSearch-MCP.md)

**[packative/naver-searchad-mcp](https://github.com/packative/naver-searchad-mcp)** – 네이버 검색광고 API로 캠페인·광고그룹·키워드·통계 관리 47개 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/packative--naver-searchad-mcp.md)

**[tenacl/naver-shopping-insight-mcp](https://github.com/tenacl/naver-shopping-insight-mcp)** – 네이버 쇼핑인사이트 API로 분야별·기기별·성별·연령별 쇼핑 트렌드를 조회하는 MCP 서버입니다. · [📄 상세](servers/tenacl--naver-shopping-insight-mcp.md)

**[swift-man/naver-mcp-py](https://github.com/swift-man/naver-mcp-py)** – 네이버 검색 API 15+ 도구와 데이터랩 트렌드 분석 10개 도구를 제공하는 Python FastMCP 서버입니다. · [📄 상세](servers/swift-man--naver-mcp-py.md)

**[codivery/creir-mcp](https://github.com/codivery/creir-mcp)** – 네이버·카카오·구글 검색을 통합하고 날씨·위치·시간 기반 순위화를 수행하는 한국 특화 검색 MCP 서버입니다. · [📄 상세](servers/codivery--creir-mcp.md)

**[SongT-50/korean-news-mcp](https://github.com/SongT-50/korean-news-mcp)** – 네이버 RSS와 Google News 기반 한국 뉴스·글로벌 테크 뉴스를 API 키 없이 무료로 제공하는 MCP 서버입니다. · [📄 상세](servers/SongT-50--korean-news-mcp.md)

**[wjddusrb03/content-research-mcp](https://github.com/wjddusrb03/content-research-mcp)** – 네이버 트렌드·블로그·뉴스 검색과 파파고 번역, Unsplash 이미지를 한 번에 묶어 콘텐츠 리서치 보고서를 생성하는 MCP 서버입니다. · [📄 상세](servers/wjddusrb03--content-research-mcp.md)

**[minjems/mcp-server-naver-suite](https://github.com/minjems/mcp-server-naver-suite)** – 네이버 검색·파파고 번역·지도 지오코딩을 하나로 통합한 올인원 네이버 API MCP 서버입니다. · [📄 상세](servers/minjems--mcp-server-naver-suite.md)

**[slowdevv-shinnoah/naver-searchad-mcp](https://github.com/slowdevv-shinnoah/naver-searchad-mcp)** – 네이버 검색광고 API로 키워드 검색량·경쟁강도·연관키워드를 조회하는 MCP 서버입니다. · [📄 상세](servers/slowdevv-shinnoah--naver-searchad-mcp.md)

**[alphago2580/naver_searchad_mcp](https://github.com/alphago2580/naver_searchad_mcp)** – 네이버 검색광고 키워드 통계와 입찰가 추정을 제공하며 Claude Desktop DXT 확장을 지원하는 MCP 서버입니다. · [📄 상세](servers/alphago2580--naver_searchad_mcp.md)

**[justcoding-ys/mcp-naver-news](https://github.com/justcoding-ys/mcp-naver-news)** – 네이버 뉴스 API로 뉴스 검색·정렬·필터링을 제공하는 MCP 서버입니다. · [📄 상세](servers/justcoding-ys--mcp-naver-news.md)

**[PlatAid/kakao-keywordad-mcp](https://github.com/PlatAid/kakao-keywordad-mcp)** – 카카오 키워드광고(검색광고) 캠페인·광고그룹·키워드·성과 리포트를 조회·분석하는 MCP 서버입니다. · [📄 상세](servers/PlatAid--kakao-keywordad-mcp.md)

**[floatingcloud/naver-search-mcp-fixed](https://github.com/floatingcloud/naver-search-mcp-fixed)** – 네이버 검색·데이터랩 트렌드를 제공하는 isnow890/naver-search-mcp의 프로토콜 오류 수정 포크입니다. · [📄 상세](servers/floatingcloud--naver-search-mcp-fixed.md)

**[leeyseo/serper-discover-mcp](https://github.com/leeyseo/serper-discover-mcp)** – Serper 구글검색에 네이버 블로그·카페 검색과 장소 발굴(discover_places)을 더한 한국 특화 검색 MCP 서버입니다. · [📄 상세](servers/leeyseo--serper-discover-mcp.md)

**[riileyy/naver-mcp](https://github.com/riileyy/naver-mcp)** – 네이버 실시간 검색을 제공하는 MCP 서버입니다. · [📄 상세](servers/riileyy--naver-mcp.md)

---

### 🌏 Tourism & Travel

> 한국 관광지, 지역 여행 정보, 방문자 서비스 관련 MCP 서버 · MCP servers for Korean tourism, travel, and visitor services.

**[harimkang/mcp-korea-tourism-api](https://github.com/harimkang/mcp-korea-tourism-api)** – 한국관광공사 TourAPI를 기반으로 관광지·행사·숙박·맛집 정보를 검색하는 MCP 서버입니다. · [📄 상세](servers/harimkang--mcp-korea-tourism-api.md)

**[pjookim/mcp-visit-korea](https://github.com/pjookim/mcp-visit-korea)** – 지역·키워드·위치 기반으로 한국 관광 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/pjookim--mcp-visit-korea.md)

**[bb4rjfl/korea-trip-concierge](https://github.com/bb4rjfl/korea-trip-concierge)** – 한국을 방문하는 외국인을 위해 장소·외국인 친화 매장·교통·결제 정보를 구조화해 제공하는 MCP 서버입니다. · [📄 상세](servers/bb4rjfl--korea-trip-concierge.md)

**[InSIkHwang/Naver-Flight-MCP](https://github.com/InSIkHwang/Naver-Flight-MCP)** – 네이버 항공권 검색 API로 직항·왕복 최저가 항공권 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/InSIkHwang--Naver-Flight-MCP.md)

---

### 📊 Public Data

> 한국 공공데이터, 지역 통계, 교통, 보건 관련 MCP 서버 · MCP servers for Korean public data, regional statistics, transport, and health.

**[pinnaclesoft-ko/be-node-seoul-data-mcp](https://github.com/pinnaclesoft-ko/be-node-seoul-data-mcp)** – 서울시 공공데이터 API(지하철 승하차·문화행사 등)를 조회하는 MCP 서버 예제입니다. · [📄 상세](servers/pinnaclesoft-ko--be-node-seoul-data-mcp.md)

**[Koomook/data-go-mcp-servers](https://github.com/Koomook/data-go-mcp-servers)** – data.go.kr 기반의 사업자등록 상태조회, 조달·계약, 금융정보 등 다양한 공공데이터 API를 개별 MCP 서버 패키지로 제공하는 프로젝트입니다. · [📄 상세](servers/Koomook--data-go-mcp-servers.md)

**[isnow890/data4library-mcp](https://github.com/isnow890/data4library-mcp)** – 도서관정보나루 API를 연동해 공공도서관 검색, 대출 현황, 독서 통계를 제공하는 MCP 서버입니다. · [📄 상세](servers/isnow890--data4library-mcp.md)

**[slicequeue/k-mfds-fooddb-mcp-server](https://github.com/slicequeue/k-mfds-fooddb-mcp-server)** – 식약처 식품영양성분 DB OpenAPI를 검색·조회할 수 있는 MCP 서버입니다. · [📄 상세](servers/slicequeue--k-mfds-fooddb-mcp-server.md)

**[slicequeue/k-targo-subway-mcp-server](https://github.com/slicequeue/k-targo-subway-mcp-server)** – 국토교통부 TAGO 지하철정보 API 기반으로 역 검색·시간표 조회를 제공하는 MCP 서버입니다. · [📄 상세](servers/slicequeue--k-targo-subway-mcp-server.md)

**[hjsh200219/korea-public-data-mcp](https://github.com/hjsh200219/korea-public-data-mcp)** – 국가법령정보센터, DART, 공공데이터포털 API를 통합해 법령·판례·기업공시·생활정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/hjsh200219--korea-public-data-mcp.md)

**[jayjodev/vivory-mcp](https://github.com/jayjodev/vivory-mcp)** – KOSIS 통계를 비롯한 한국 공공데이터를 MCP 서버 패키지로 제공하는 Vivory 기반 프로젝트입니다. · [📄 상세](servers/jayjodev--vivory-mcp.md)

**[jaykim429/korea-statistic-MCP-cginside](https://github.com/jaykim429/korea-statistic-MCP-cginside)** – KOSIS OpenAPI를 자연어 질의, 통계 조회, 분석, SVG 시각화로 연결하는 MCP 서버입니다. · [📄 상세](servers/jaykim429--korea-statistic-MCP-cginside.md)

**[Dayoooun/korea-stats-mcp](https://github.com/Dayoooun/korea-stats-mcp)** – KOSIS OpenAPI 기반으로 한국 통계를 자연어로 검색·분석하는 MCP 서버입니다. · [📄 상세](servers/Dayoooun--korea-stats-mcp.md)

**[ceami/opendata-mcp](https://github.com/ceami/opendata-mcp)** – 공공데이터포털 OpenAPI를 검색하고 표준 문서 기반으로 API를 호출하는 MCP 서버입니다. · [📄 상세](servers/ceami--opendata-mcp.md)

**[k08200/korea-mcp-suite](https://github.com/k08200/korea-mcp-suite)** – 기상청·서울시·국토교통부·행정안전부 공공데이터를 연동해 날씨·지하철·버스·부동산 실거래가·도로명주소 등 10가지 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/k08200--korea-mcp-suite.md)

**[SongT-50/korean-public-data-mcp](https://github.com/SongT-50/korean-public-data-mcp)** – 날씨·부동산 실거래가·대기질·경제통계·사업자조회 등 한국 5대 공공데이터를 AI에 연결하는 MCP 서버입니다. · [📄 상세](servers/SongT-50--korean-public-data-mcp.md)

**[jinny-han/industrial-complex-api-mcp](https://github.com/jinny-han/industrial-complex-api-mcp)** – 전국 1,428개 산업단지 정보를 자연어로 검색·조회하는 MCP 서버입니다. · [📄 상세](servers/jinny-han--industrial-complex-api-mcp.md)

**[pianovirus/kfda-mcp](https://github.com/pianovirus/kfda-mcp)** – 식약처 OpenAPI와 DUR 안전규칙으로 의약품 검색, 병용금기 확인, 건강기능식품 조회를 제공하는 MCP 서버입니다. · [📄 상세](servers/pianovirus--kfda-mcp.md)

**[SilverQ/kipris-mcp](https://github.com/SilverQ/kipris-mcp)** – KIPRIS Plus Open API로 한국 특허·상표 등 지식재산 데이터를 검색·조회하는 MCP 서버입니다. · [📄 상세](servers/SilverQ--kipris-mcp.md)

**[opendata-kr/narajangteo-prespec-mcp](https://github.com/opendata-kr/narajangteo-prespec-mcp)** – 나라장터 사전규격정보서비스(data.go.kr) API를 자연어로 검색·조회하는 MCP 서버입니다. · [📄 상세](servers/opendata-kr--narajangteo-prespec-mcp.md)

**[opendata-kr/narajangteo-bid-mcp](https://github.com/opendata-kr/narajangteo-bid-mcp)** – 나라장터 입찰공고정보서비스(data.go.kr) API로 공공조달 입찰공고를 자연어 검색하는 MCP 서버입니다. · [📄 상세](servers/opendata-kr--narajangteo-bid-mcp.md)

**[vertical-mcp/kolas-mcp](https://github.com/vertical-mcp/kolas-mcp)** – 국가기술표준원(KATS) 산하 KOLAS 공인 교정·시험·검사 기관 정보를 검색하는 MCP 서버입니다. · [📄 상세](servers/vertical-mcp--kolas-mcp.md)

**[kwanGDss/mcp-bizinfo](https://github.com/kwanGDss/mcp-bizinfo)** – 기업마당(Bizinfo) 지원사업 데이터를 지역·대상·키워드·자연어로 검색하는 MCP 서버입니다. · [📄 상세](servers/kwanGDss--mcp-bizinfo.md)

**[alphago2580/naramarketmcp](https://github.com/alphago2580/naramarketmcp)** – 조달청 나라장터(G2B) OPEN API로 입찰공고·낙찰·계약·조달통계·쇼핑몰 상품을 조회하는 15개 도구 MCP 서버입니다. · [📄 상세](servers/alphago2580--naramarketmcp.md)

**[Tech-curator/korean-patent-mcp](https://github.com/Tech-curator/korean-patent-mcp)** – KIPRIS 특허정보 API로 출원인별 특허검색·상세조회·인용특허 분석을 제공하는 MCP 서버입니다. · [📄 상세](servers/Tech-curator--korean-patent-mcp.md)

**[Won-ahamada/KERIS_EDUmcp](https://github.com/Won-ahamada/KERIS_EDUmcp)** – 학교알리미 API(17종)와 RISS 학술 API를 TOON 파일로 확장하는 18개 도구 한국 교육데이터 MCP 서버입니다. · [📄 상세](servers/Won-ahamada--KERIS_EDUmcp.md)

**[seolcoding/korean-stat-mcp](https://github.com/seolcoding/korean-stat-mcp)** – KOSIS OpenAPI 통계 데이터를 검색·조회·분석할 수 있게 제공하는 Python MCP 서버입니다. · [📄 상세](servers/seolcoding--korean-stat-mcp.md)

---

### 🌦 Weather

> 한국 기상청 및 한국 날씨 데이터 관련 MCP 서버 · MCP servers for Korea Meteorological Administration (KMA) and weather data.

**[woongaro/KMA-WEATHER-MCP](https://github.com/woongaro/KMA-WEATHER-MCP)** – 기상청 단기예보 OpenAPI로 현재 날씨와 예보 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/woongaro--KMA-WEATHER-MCP.md)

**[ohhan777/korea_weather](https://github.com/ohhan777/korea_weather)** – 기상청 단기예보 API를 연동해 한국 날씨 정보를 제공하는 MCP 서버입니다. · [📄 상세](servers/ohhan777--korea_weather.md)

**[worker-ants/korea-weather-mcp](https://github.com/worker-ants/korea-weather-mcp)** – 기상청 API 허브의 단기예보·중기예보·기상특보·영향예보·구역정보를 제공하는 MCP 서버입니다. · [📄 상세](servers/worker-ants--korea-weather-mcp.md)

**[Kinuk97/mcp-get-weather](https://github.com/Kinuk97/mcp-get-weather)** – 기상청 단기예보 실황 API 기반으로 현재 한국 날씨를 조회하는 MCP 서버입니다. · [📄 상세](servers/Kinuk97--mcp-get-weather.md)

**[jikime/mcp-weather](https://github.com/jikime/mcp-weather)** – 기상청 단기예보 API로 지역 검색 기반 한국 날씨 정보를 제공하는 MCP 서버입니다. · [📄 상세](servers/jikime--mcp-weather.md)

**[dbsxortime/mcp-weather-server](https://github.com/dbsxortime/mcp-weather-server)** – 한국 기상청 API를 활용해 위치 기반 현재 날씨와 예보를 제공하는 MCP 서버입니다. · [📄 상세](servers/dbsxortime--mcp-weather-server.md)

**[sunhye/mcp-korea-weather](https://github.com/sunhye/mcp-korea-weather)** – 기상청(KMA) API로 실황·초단기예보(기온·강수·바람·습도)를 제공하는 Fastify/Node 기반 MCP 서버입니다. · [📄 상세](servers/sunhye--mcp-korea-weather.md)

---

### 🔤 Korean NLP & Language

> 한국어 자연어 처리, 형태소 분석, 사전, 문서 파싱 관련 MCP 서버 · MCP servers for Korean NLP, dictionaries, and document parsing.

**[dahlia/ko-stdict-mcp](https://github.com/dahlia/ko-stdict-mcp)** – 표준국어대사전 전체 데이터를 SQLite에 저장해 레이트 리미트 없이 표제어·뜻풀이·발음·용례를 빠르게 조회하는 MCP 서버입니다. · [📄 상세](servers/dahlia--ko-stdict-mcp.md)

**[chrisryugj/kordoc](https://github.com/chrisryugj/kordoc)** – 한글(HWP, HWPX) 및 PDF 문서를 파싱해 텍스트·마크다운으로 변환하며 문서 비교·표 추출·양식 인식 등 7가지 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/chrisryugj--kordoc.md)

**[winterjung/mcp-korean-spell](https://github.com/winterjung/mcp-korean-spell)** – 한국어 맞춤법과 문법 오류를 교정하는 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/winterjung--mcp-korean-spell.md)

**[ai-screams/HwpForge](https://github.com/ai-screams/HwpForge)** – 한글 HWPX 문서를 Markdown과 상호 변환하고 JSON 편집·검증하는 9가지 도구를 제공하는 Rust 기반 MCP 서버입니다. · [📄 상세](servers/ai-screams--HwpForge.md)

**[Dayoooun/hwpx-mcp](https://github.com/Dayoooun/hwpx-mcp)** – 한글 HWPX 문서를 표·문단·스타일·이미지까지 읽기·생성·편집하는 강화 MCP 서버입니다. · [📄 상세](servers/Dayoooun--hwpx-mcp.md)

**[sinmb79/GongMun-Doctor-MCP](https://github.com/sinmb79/GongMun-Doctor-MCP)** – 공문서(.hwpx/.hwp)를 3단계 AI 교정으로 맞춤법·문법·공문 문체를 로컬에서 교정하는 MCP 서버입니다. · [📄 상세](servers/sinmb79--GongMun-Doctor-MCP.md)

**[crowwan/hwp-mcp-advanced-custom](https://github.com/crowwan/hwp-mcp-advanced-custom)** – 한글(HWP) 문서를 59개 기능으로 생성·편집·서식·표·PDF 변환까지 제어하는 고도화 MCP 서버입니다. · [📄 상세](servers/crowwan--hwp-mcp-advanced-custom.md)

**[skerishKang/33MCP_HWP_Limone](https://github.com/skerishKang/33MCP_HWP_Limone)** – 한글(HWP) 문서를 문서관리부터 고급 서식·표까지 제어하는 고도화 MCP 서버입니다. · [📄 상세](servers/skerishKang--33MCP_HWP_Limone.md)

**[beomzh/hwpConverMdMCP](https://github.com/beomzh/hwpConverMdMCP)** – HWP/HWPX 파일을 Markdown으로 변환하는 hwpConverMd API의 MCP 서버입니다. · [📄 상세](servers/beomzh--hwpConverMdMCP.md)

**[rgbcap/hwpx-mcp-server](https://github.com/rgbcap/hwpx-mcp-server)** – 한글 .hwpx 파일 텍스트 추출·찾아바꾸기·스타일 변경을 제공하는 MCP 서버입니다. · [📄 상세](servers/rgbcap--hwpx-mcp-server.md)

**[devRonPark/kakao-playmcp](https://github.com/devRonPark/kakao-playmcp)** – 한국어 카카오톡 문장을 자연스러운 일본어로 변환·교정하고 학습 카드를 제공하는 일본어 코치 MCP 서버입니다. · [📄 상세](servers/devRonPark--kakao-playmcp.md)

**[airmang/hwpx-mcp-server](https://github.com/airmang/hwpx-mcp-server)** – 한글(HWPX) 문서를 한컴오피스 없이 순수 파이썬으로 읽기·검색·편집·양식채움·생성·검증하는 MCP 서버입니다. · [📄 상세](servers/airmang--hwpx-mcp-server.md)

---

### 🤝 Collaboration & Communication

> 한국 협업 도구, 메신저, 업무 관리 서비스 관련 MCP 서버 · MCP servers for Korean collaboration tools and messengers.

**[dooray-go/dooray_mcp](https://github.com/dooray-go/dooray_mcp)** – Dooray! 메신저 보내기, 캘린더 조회 및 일정 등록 기능을 제공하는 MCP 서버입니다. · [📄 상세](servers/dooray-go--dooray_mcp.md)

**[kwanok/dooray-mcp](https://github.com/kwanok/dooray-mcp)** – Dooray 업무·댓글·마일스톤·태그·멤버·메신저 기능을 포함한 32개 도구를 제공하는 MCP 서버입니다. · [📄 상세](servers/kwanok--dooray-mcp.md)

**[mskim8717/dooray-mcp](https://github.com/mskim8717/dooray-mcp)** – Dooray API를 활용해 일정 추가 및 관리를 지원하는 MCP 서버입니다. · [📄 상세](servers/mskim8717--dooray-mcp.md)

**[hyeri0903/naver-works-mcp](https://github.com/hyeri0903/naver-works-mcp)** – 네이버 웍스(Naver Works) API를 연동하는 MCP 서버입니다. · [📄 상세](servers/hyeri0903--naver-works-mcp.md)

**[youngsooco/k-mail-mcp](https://github.com/youngsooco/k-mail-mcp)** – 네이버·다음/카카오·Gmail·네이트·야후·iCloud 6개 메일을 Claude에 연결해 요약·관리하는 MCP 서버입니다. · [📄 상세](servers/youngsooco--k-mail-mcp.md)

**[mwl313/KatokMCP](https://github.com/mwl313/KatokMCP)** – 카카오톡을 제어해 대화 읽기·메시지 전송·채팅방 목록 관리를 수행하는 MCP 서버입니다. · [📄 상세](servers/mwl313--KatokMCP.md)

**[tallpizza/dooray-mcp](https://github.com/tallpizza/dooray-mcp)** – Dooray API를 6개 통합 도구로 묶어 업무·댓글·태그·검색을 관리하는 MCP 서버입니다. · [📄 상세](servers/tallpizza--dooray-mcp.md)

**[inspirit941/kakao-bot-mcp-server](https://github.com/inspirit941/kakao-bot-mcp-server)** – 카카오 Developers API(카카오톡 메시지 전송·톡캘린더)를 AI 에이전트에 통합하는 MCP 서버입니다. · [📄 상세](servers/inspirit941--kakao-bot-mcp-server.md)

---

### 🧩 Miscellaneous

> 위 카테고리에 속하지 않는 기타 한국 생태계 관련 MCP 서버 · Other Korea-specific MCP servers.

**[carasjung/kr-movie-tv-mcp](https://github.com/carasjung/kr-movie-tv-mcp)** – 한국 영화와 드라마의 박스오피스, 시청률, 수상 이력, 스트리밍 제공 여부, 출연진 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/carasjung--kr-movie-tv-mcp.md)

**[bb4rjfl/saju-concierge](https://github.com/bb4rjfl/saju-concierge)** – 생년월일시로 사주 명식을 계산해 운세·궁합·이름풀이·타로를 제공하는 MCP 서버입니다. · [📄 상세](servers/bb4rjfl--saju-concierge.md)

**[kmjm231/korea-scholar-mcp](https://github.com/kmjm231/korea-scholar-mcp)** – 한국 학술지 논문을 검색하고 상세 정보를 조회하는 MCP 서버입니다. · [📄 상세](servers/kmjm231--korea-scholar-mcp.md)

**[man2service/taxfood-mcp](https://github.com/man2service/taxfood-mcp)** – 공공기관 업무추진비 식당 데이터를 검색·지역별·랭킹으로 조회하는 MCP 서버입니다. · [📄 상세](servers/man2service--taxfood-mcp.md)

**[MUSE-CODE-SPACE/content-genie-mcp](https://github.com/MUSE-CODE-SPACE/content-genie-mcp)** – 네이버·다음·유튜브 등 실시간 트렌드와 100여 개 한국 기념일 DB, 바이럴 점수 예측을 제공하는 한국 크리에이터용 MCP 서버입니다. · [📄 상세](servers/MUSE-CODE-SPACE--content-genie-mcp.md)

**[choec77/mcp](https://github.com/choec77/mcp)** – 네이버 클라우드 플랫폼(NCP) 인프라를 자연어로 생성·조회·관리하는 MCP 서버입니다. · [📄 상세](servers/choec77--mcp.md)

**[dangamsoft/cafe-mcp](https://github.com/dangamsoft/cafe-mcp)** – 한국 사주명리(오행·격국·용신) 분석을 OWL 온톨로지 기반으로 제공하는 MCP 서버입니다. · [📄 상세](servers/dangamsoft--cafe-mcp.md)

**[xrissohn/nori-buddy-mcp](https://github.com/xrissohn/nori-buddy-mcp)** – 카카오톡 안에서 대화하는 성장형 AI 캐릭터 친구(카카오 PlayMCP 제출작) MCP 서버입니다. · [📄 상세](servers/xrissohn--nori-buddy-mcp.md)

**[re-rank/UIUX-MCP](https://github.com/re-rank/UIUX-MCP)** – 정부 표준 디자인시스템 KRDS 컴포넌트 검색·HTML 코드 삽입·디자인토큰 조회·접근성/준수 검증을 제공하는 9개 도구 MCP 서버입니다. · [📄 상세](servers/re-rank--UIUX-MCP.md)

---

## 기여 방법 (Contributing)

기여를 환영합니다. 프로젝트를 추가하려면 [CONTRIBUTING.md](CONTRIBUTING.md)를 먼저 읽어주세요.

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a project.

---

## 라이선스 (License)

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

이 목록은 [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) 라이선스 하에 공개됩니다.

This list is released under the [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) license.
