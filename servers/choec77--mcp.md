# mcp (NCP MCP Server)

> **[choec77/mcp](https://github.com/choec77/mcp)** · ⭐ N/A · TypeScript · 카테고리: 🧩 Miscellaneous

네이버 클라우드 플랫폼(NCP) 인프라를 자연어로 생성·조회·관리하는 MCP 서버입니다.

## 개요

네이버 클라우드 플랫폼(NCP)의 인프라를 Claude Desktop과 연동해 대화형으로 관리하는 TypeScript MCP 서버다. 서버 인스턴스, VPC/Subnet/ACG 네트워크, Load Balancer, Cloud DB를 자연어로 생성·조회·삭제·관리한다. NCP REST API를 HMAC-SHA256 서명 방식으로 호출한다.

## 제공 도구

| 도구 | 기능 |
|------|------|
| `list_servers` / `get_server_detail` | 서버 인스턴스 목록·상세 조회 |
| `create_server` / `start_server` / `stop_server` / `delete_server` | 서버 생성·시작·중지·삭제 |
| `list_vpcs` / `create_vpc` / `delete_vpc` | VPC 조회·생성·삭제 |
| `list_subnets` / `create_subnet` / `delete_subnet` | Subnet 조회·생성·삭제 |
| `list_acgs` / `create_acg` / `delete_acg` / `add_acg_rule` | ACG 조회·생성·삭제·인바운드 규칙 추가 |
| `list_load_balancers` / `create_load_balancer` / `delete_load_balancer` / `add_load_balancer_target` | 로드밸런서 조회·생성·삭제·타겟 추가 |
| `list_cloud_dbs` / `create_cloud_db` / `delete_cloud_db` | Cloud DB 조회·생성·삭제 |

## 설치

```bash
git clone https://github.com/choec77/mcp.git
cd mcp
npm install
npm run build
```

## 필요 키 · 환경변수

| 환경변수 | 발급처 | 필수 |
|---------|--------|------|
| `NCP_ACCESS_KEY` | [네이버 클라우드 플랫폼](https://www.ncloud.com) 계정 관리 → 인증키 | ✅ |
| `NCP_SECRET_KEY` | 위와 동일 | ✅ |

## 설정 예시

```json
{
  "mcpServers": {
    "ncp-compute": {
      "command": "node",
      "args": ["/path/to/ncp-compute-mcp-server/dist/index.js"],
      "env": {
        "NCP_ACCESS_KEY": "your_access_key",
        "NCP_SECRET_KEY": "your_secret_key"
      }
    }
  }
}
```

## 비고

- 인증은 HMAC-SHA256 서명 방식. 저장소명은 `mcp`이나 프로젝트 이름은 "NCP MCP Server".
- 향후 계획: Object Storage, Monitoring(Cloud Insight), Auto Scaling, Block Storage API 추가.

---
*수집일: 2026-07-03 · 출처: 저장소 README*
