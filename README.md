# Awesome MCP Korea (mcp-all-korea)

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Servers](https://img.shields.io/badge/servers-56-blue)
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
  - [📜 Legal & Government](#-legal--government) · 법률·정부 (9)
  - [🛒 Commerce & Retail](#-commerce--retail) · 커머스 (2)
  - [🏦 Finance & Tax](#-finance--tax) · 금융·세금 (8)
  - [🏠 Real Estate](#-real-estate) · 부동산 (3)
  - [🗺 Maps & Address](#-maps--address) · 지도·주소 (6)
  - [🔎 Search & Trends](#-search--trends) · 검색·트렌드 (2)
  - [🌏 Tourism & Travel](#-tourism--travel) · 관광·여행 (2)
  - [📊 Public Data](#-public-data) · 공공데이터·지역 (10)
  - [🌦 Weather](#-weather) · 날씨 (6)
  - [🔤 Korean NLP & Language](#-korean-nlp--language) · 한국어 (3)
  - [🤝 Collaboration & Communication](#-collaboration--communication) · 협업 (4)
  - [🧩 Miscellaneous](#-miscellaneous) · 기타 (1)
- [기여 방법 (Contributing)](#기여-방법-contributing)
- [라이선스 (License)](#라이선스-license)
- [관련 프로젝트 (Related Projects)](#관련-프로젝트-related-projects)

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

**[chrisryugj/korean-law-mcp](https://github.com/chrisryugj/korean-law-mcp)** – 국가법령정보 Open API를 기반으로 법령·판례·행정규칙 등을 검색·조회·분석하는 MCP 서버입니다.

**[ChangooLee/mcp-kr-legislation](https://github.com/ChangooLee/mcp-kr-legislation)** – 법제처 OPEN API를 통합해 법령·판례·행정규칙·자치법규·조약·별표서식 등 한국 법률 정보를 조회하는 MCP 서버입니다.

**[hollobit/assembly-api-mcp](https://github.com/hollobit/assembly-api-mcp)** – 대한민국 국회 Open API와 국민참여입법센터·NABO API를 연동해 국회의원·의안·일정·회의록·청원·예산정책처 자료를 조회하는 MCP 서버입니다.

**[finalchild/law-mcp](https://github.com/finalchild/law-mcp)** – open.law.go.kr API를 통해 한국 법령 데이터를 조회하는 MCP 서버입니다.

**[DrMoony/koregx](https://github.com/DrMoony/koregx)** – 한국 헬스케어 법령, 행정해석, 식약처·복지부 행정규칙, HIRA 결정을 통합 조회하는 웹 서비스 및 MCP 서버입니다.

**[seung23/lawtutor-mcp](https://github.com/seung23/lawtutor-mcp)** – 국가법령정보센터 데이터를 기반으로 7급 공무원시험 행정법·헌법 학습용 RAG 검색 도구를 제공하는 MCP 서버입니다.

**[rabqatab/LexLink-ko-mcp](https://github.com/rabqatab/LexLink-ko-mcp)** – 국가법령정보센터 Open API 기반으로 법령·판례·행정규칙·헌재결정례·행정심판례를 구조적으로 제공하고 시맨틱 검색(aiSearch)을 지원하는 MCP 서버입니다.

**[SeoNaRu/korean-law-mcp](https://github.com/SeoNaRu/korean-law-mcp)** – 국가법령정보센터 Open API로 한국 법령·판례·행정규칙 검색을 제공하는 MCP 서버입니다.

**[workbookbulb863/korean-law-alio-mcp](https://github.com/workbookbulb863/korean-law-alio-mcp)** – 국가법령정보센터와 ALIO 공공기관 내부규정을 함께 검색·비교·분석하는 MCP 서버입니다.

---

### 🛒 Commerce & Retail

> 한국 전자상거래, 오픈마켓, 쇼핑 서비스 관련 MCP 서버 · MCP servers for Korean e-commerce, open markets, and shopping.

**[hmmhmmhm/daiso-mcp](https://github.com/hmmhmmhm/daiso-mcp)** – 주변 다이소 매장을 검색하고 원하는 상품의 재고 여부 및 가격을 조회하는 MCP 서버입니다.

**[edward-kim-dev/kr-pc-deals-mcp](https://github.com/edward-kim-dev/kr-pc-deals-mcp)** – 다나와·컴퓨존 PC 부품 최저가 검색, 가격 비교, 가격 이력, 빌드 견적, CPU-메인보드-RAM 호환성 체크를 제공하는 MCP 서버입니다.

---

### 🏦 Finance & Tax

> 한국 금융, 세금, 주식, 암호화폐 관련 MCP 서버 · MCP servers for Korean finance, tax, stocks, and crypto.

**[migusdn/KIS_MCP_Server](https://github.com/migusdn/KIS_MCP_Server)** – 한국투자증권(KIS) REST API를 통해 국내·해외 주식 시세 조회와 주문 기능을 제공하는 MCP 서버입니다.

**[Mrbaeksang/korea-stock-analyzer-mcp](https://github.com/Mrbaeksang/korea-stock-analyzer-mcp)** – 한국 주식의 재무·기술지표·DCF·뉴스·수급을 통합 분석하는 MCP 서버입니다.

**[jjlabsio/korea-stock-mcp](https://github.com/jjlabsio/korea-stock-mcp)** – DART와 KRX 공식 API를 연동해 공시·재무제표·주가 데이터를 조회하는 한국 주식 분석 MCP 서버입니다.

**[aesthetic-legalism5470/korean-dart-mcp](https://github.com/aesthetic-legalism5470/korean-dart-mcp)** – OpenDART API를 기반으로 공시·재무·지분·XBRL 데이터를 조회하고 첨부 문서를 처리하는 MCP 서버입니다.

**[koreainvestment/koreainvestment-mcp](https://github.com/koreainvestment/koreainvestment-mcp)** – 한국투자증권 API를 자연어로 검색해 필요한 금융 API를 찾을 수 있는 MCP 서버입니다.

**[sharebook-kr/pykrx-mcp](https://github.com/sharebook-kr/pykrx-mcp)** – pykrx 라이브러리 기반으로 KOSPI·KOSDAQ·KONEX 주가, 재무제표, 투자자별 수급 및 공매도 데이터를 제공하는 MCP 서버입니다.

**[redoxnet/mcp-lsopenapi](https://github.com/redoxnet/mcp-lsopenapi)** – LS증권 OpenAPI를 통해 국내 주식 시세, 차트, 지표 데이터를 자연어 도구로 조회하는 MCP 서버입니다.

**[snaiws/DART-mcp-server](https://github.com/snaiws/DART-mcp-server)** – 금융감독원 DART API를 활용해 상장기업 공시, 기업 개황, 재무 정보 등을 조회하는 MCP 서버입니다.

---

### 🏠 Real Estate

> 한국 부동산 실거래가, 등기, 청약, 투자분석 관련 MCP 서버 · MCP servers for Korean real estate, transactions, and housing subscriptions.

**[gum798/A2A-MCP-RealEstate](https://github.com/gum798/A2A-MCP-RealEstate)** – 국토부 실거래가와 위치 데이터를 바탕으로 투자가치·삶의질을 종합 평가하는 한국 부동산 추천 MCP 서버입니다.

**[ChangooLee/mcp-kr-realestate](https://github.com/ChangooLee/mcp-kr-realestate)** – 국토부 실거래가와 ECOS 등 공공 API를 통합해 한국 부동산 투자 분석을 수행하는 MCP 서버입니다.

**[tae0y/real-estate-mcp](https://github.com/tae0y/real-estate-mcp)** – 국토교통부·온비드·청약홈 데이터를 기반으로 한국 부동산 매매·전월세·청약 정보를 제공하는 MCP 서버입니다.

---

### 🗺 Maps & Address

> 한국 지도, 주소, 좌표, 길찾기, 지역 위치 서비스 관련 MCP 서버 · MCP servers for Korean maps, addresses, geocoding, and routing.

**[flor3z-github/navermap-mcp-server](https://github.com/flor3z-github/navermap-mcp-server)** – 네이버 클라우드 Maps API를 통해 주소·좌표 변환(지오코딩/역지오코딩), 경로 탐색, 정적 지도 이미지 생성, API 사용량 조회 기능을 제공하는 MCP 서버입니다.

**[yeonupark/mcp-naver-map](https://github.com/yeonupark/mcp-naver-map)** – NCP Geolocation API와 Directions15 API를 연동해 IP 기반 위치 조회 및 드라이빙 경로 탐색을 제공하는 MCP 서버입니다.

**[yunkee-lee/mcp-naver-maps](https://github.com/yunkee-lee/mcp-naver-maps)** – 네이버 지도 API(지오코딩)와 네이버 검색 API(로컬 검색)를 연동하는 MCP 서버입니다.

**[CaChiJ/kakao-navigation-mcp-server](https://github.com/CaChiJ/kakao-navigation-mcp-server)** – 카카오 모빌리티 및 카카오맵 API를 연동해 위치 검색(지오코딩)과 도보·자동차 길찾기 서비스를 제공하는 MCP 서버입니다.

**[jeong-sik/kakao-api-mcp-server](https://github.com/jeong-sik/kakao-api-mcp-server)** – 카카오맵 API와 Daum 검색 API를 연동해 장소 검색, 좌표-주소 변환, 길찾기, 웹·이미지·블로그·카페 검색을 제공하는 MCP 서버입니다.

**[cgoinglove/mcp-server-kakao-map](https://github.com/cgoinglove/mcp-server-kakao-map)** – 카카오맵 API 키워드 검색을 통해 한국 내 식당·카페·관광명소 등 장소를 추천하는 MCP 서버입니다.

---

### 🔎 Search & Trends

> 한국 검색 포털 및 트렌드 데이터 분석 관련 MCP 서버 · MCP servers for Korean search portals and trend analysis.

**[isnow890/naver-search-mcp](https://github.com/isnow890/naver-search-mcp)** – 네이버 검색 API와 데이터랩 API를 연동해 한국 서비스 특화 검색·트렌드 분석을 제공하는 MCP 서버입니다.

**[jikime/py-mcp-naver-search](https://github.com/jikime/py-mcp-naver-search)** – 네이버 검색 API로 다양한 콘텐츠 검색 결과를 LLM이 처리하기 쉬운 구조화된 텍스트로 제공하는 MCP 서버입니다.

---

### 🌏 Tourism & Travel

> 한국 관광지, 지역 여행 정보, 방문자 서비스 관련 MCP 서버 · MCP servers for Korean tourism, travel, and visitor services.

**[harimkang/mcp-korea-tourism-api](https://github.com/harimkang/mcp-korea-tourism-api)** – 한국관광공사 TourAPI를 기반으로 관광지·행사·숙박·맛집 정보를 검색하는 MCP 서버입니다.

**[pjookim/mcp-visit-korea](https://github.com/pjookim/mcp-visit-korea)** – 지역·키워드·위치 기반으로 한국 관광 정보를 조회하는 MCP 서버입니다.

---

### 📊 Public Data

> 한국 공공데이터, 지역 통계, 교통, 보건 관련 MCP 서버 · MCP servers for Korean public data, regional statistics, transport, and health.

**[pinnaclesoft-ko/be-node-seoul-data-mcp](https://github.com/pinnaclesoft-ko/be-node-seoul-data-mcp)** – 서울시 공공데이터 API(지하철 승하차·문화행사 등)를 조회하는 MCP 서버 예제입니다.

**[Koomook/data-go-mcp-servers](https://github.com/Koomook/data-go-mcp-servers)** – data.go.kr 기반의 사업자등록 상태조회, 조달·계약, 금융정보 등 다양한 공공데이터 API를 개별 MCP 서버 패키지로 제공하는 프로젝트입니다.

**[isnow890/data4library-mcp](https://github.com/isnow890/data4library-mcp)** – 도서관정보나루 API를 연동해 공공도서관 검색, 대출 현황, 독서 통계를 제공하는 MCP 서버입니다.

**[slicequeue/k-mfds-fooddb-mcp-server](https://github.com/slicequeue/k-mfds-fooddb-mcp-server)** – 식약처 식품영양성분 DB OpenAPI를 검색·조회할 수 있는 MCP 서버입니다.

**[slicequeue/k-targo-subway-mcp-server](https://github.com/slicequeue/k-targo-subway-mcp-server)** – 국토교통부 TAGO 지하철정보 API 기반으로 역 검색·시간표 조회를 제공하는 MCP 서버입니다.

**[hjsh200219/korea-public-data-mcp](https://github.com/hjsh200219/korea-public-data-mcp)** – 국가법령정보센터, DART, 공공데이터포털 API를 통합해 법령·판례·기업공시·생활정보를 조회하는 MCP 서버입니다.

**[jayjodev/vivory-mcp](https://github.com/jayjodev/vivory-mcp)** – KOSIS 통계를 비롯한 한국 공공데이터를 MCP 서버 패키지로 제공하는 Vivory 기반 프로젝트입니다.

**[jaykim429/korea-statistic-MCP-cginside](https://github.com/jaykim429/korea-statistic-MCP-cginside)** – KOSIS OpenAPI를 자연어 질의, 통계 조회, 분석, SVG 시각화로 연결하는 MCP 서버입니다.

**[Dayoooun/korea-stats-mcp](https://github.com/Dayoooun/korea-stats-mcp)** – KOSIS OpenAPI 기반으로 한국 통계를 자연어로 검색·분석하는 MCP 서버입니다.

**[ceami/opendata-mcp](https://github.com/ceami/opendata-mcp)** – 공공데이터포털 OpenAPI를 검색하고 표준 문서 기반으로 API를 호출하는 MCP 서버입니다.

---

### 🌦 Weather

> 한국 기상청 및 한국 날씨 데이터 관련 MCP 서버 · MCP servers for Korea Meteorological Administration (KMA) and weather data.

**[woongaro/KMA-WEATHER-MCP](https://github.com/woongaro/KMA-WEATHER-MCP)** – 기상청 단기예보 OpenAPI로 현재 날씨와 예보 도구를 제공하는 MCP 서버입니다.

**[ohhan777/korea_weather](https://github.com/ohhan777/korea_weather)** – 기상청 단기예보 API를 연동해 한국 날씨 정보를 제공하는 MCP 서버입니다.

**[worker-ants/korea-weather-mcp](https://github.com/worker-ants/korea-weather-mcp)** – 기상청 API 허브의 단기예보·중기예보·기상특보·영향예보·구역정보를 제공하는 MCP 서버입니다.

**[Kinuk97/mcp-get-weather](https://github.com/Kinuk97/mcp-get-weather)** – 기상청 단기예보 실황 API 기반으로 현재 한국 날씨를 조회하는 MCP 서버입니다.

**[jikime/mcp-weather](https://github.com/jikime/mcp-weather)** – 기상청 단기예보 API로 지역 검색 기반 한국 날씨 정보를 제공하는 MCP 서버입니다.

**[dbsxortime/mcp-weather-server](https://github.com/dbsxortime/mcp-weather-server)** – 한국 기상청 API를 활용해 위치 기반 현재 날씨와 예보를 제공하는 MCP 서버입니다.

---

### 🔤 Korean NLP & Language

> 한국어 자연어 처리, 형태소 분석, 사전, 문서 파싱 관련 MCP 서버 · MCP servers for Korean NLP, dictionaries, and document parsing.

**[dahlia/ko-stdict-mcp](https://github.com/dahlia/ko-stdict-mcp)** – 표준국어대사전 전체 데이터를 SQLite에 저장해 레이트 리미트 없이 표제어·뜻풀이·발음·용례를 빠르게 조회하는 MCP 서버입니다.

**[chrisryugj/kordoc](https://github.com/chrisryugj/kordoc)** – 한글(HWP, HWPX) 및 PDF 문서를 파싱해 텍스트·마크다운으로 변환하며 문서 비교·표 추출·양식 인식 등 7가지 도구를 제공하는 MCP 서버입니다.

**[winterjung/mcp-korean-spell](https://github.com/winterjung/mcp-korean-spell)** – 한국어 맞춤법과 문법 오류를 교정하는 도구를 제공하는 MCP 서버입니다.

---

### 🤝 Collaboration & Communication

> 한국 협업 도구, 메신저, 업무 관리 서비스 관련 MCP 서버 · MCP servers for Korean collaboration tools and messengers.

**[dooray-go/dooray_mcp](https://github.com/dooray-go/dooray_mcp)** – Dooray! 메신저 보내기, 캘린더 조회 및 일정 등록 기능을 제공하는 MCP 서버입니다.

**[kwanok/dooray-mcp](https://github.com/kwanok/dooray-mcp)** – Dooray 업무·댓글·마일스톤·태그·멤버·메신저 기능을 포함한 32개 도구를 제공하는 MCP 서버입니다.

**[mskim8717/dooray-mcp](https://github.com/mskim8717/dooray-mcp)** – Dooray API를 활용해 일정 추가 및 관리를 지원하는 MCP 서버입니다.

**[hyeri0903/naver-works-mcp](https://github.com/hyeri0903/naver-works-mcp)** – 네이버 웍스(Naver Works) API를 연동하는 MCP 서버입니다.

---

### 🧩 Miscellaneous

> 위 카테고리에 속하지 않는 기타 한국 생태계 관련 MCP 서버 · Other Korea-specific MCP servers.

**[carasjung/kr-movie-tv-mcp](https://github.com/carasjung/kr-movie-tv-mcp)** – 한국 영화와 드라마의 박스오피스, 시청률, 수상 이력, 스트리밍 제공 여부, 출연진 정보를 조회하는 MCP 서버입니다.

---

## 기여 방법 (Contributing)

기여를 환영합니다. 프로젝트를 추가하려면 [CONTRIBUTING.md](CONTRIBUTING.md)를 먼저 읽어주세요.

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a project.

---

## 라이선스 (License)

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

이 목록은 [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) 라이선스 하에 공개됩니다.

This list is released under the [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) license.

---

## 관련 프로젝트 (Related Projects)

- [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) – A curated list of MCP servers.
- [modelcontextprotocol](https://github.com/modelcontextprotocol) – Official MCP specification and SDKs.
