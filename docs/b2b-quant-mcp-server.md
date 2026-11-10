# B2B Regulatory, KYB, FinTech & SecOps MCP Server (30 Tools)

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/b2b-quant-mcp-server.html](https://jesleytassili-glitch.github.io/docs/b2b-quant-mcp-server.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/b2b-quant-mcp-server.md](https://jesleytassili-glitch.github.io/docs/b2b-quant-mcp-server.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-quant-mcp-server.json](https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-quant-mcp-server.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/b2b-quant-mcp-server](https://apify.com/b2b-quant-apis/b2b-quant-mcp-server)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646](https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/b2b-quant-mcp-server](https://rapidapi.com/b2bquantapis/api/b2b-quant-mcp-server)

## Executive Overview
Official Master Model Context Protocol (MCP) Server & Tool Router for all 30 B2B Regulatory, KYB, Sanctions AML, SEC EDGAR, SAM.gov, EU TED, UK FCA, Brazil BCB/PIX/Tax, Healthcare & SecOps engines (@b2b-quant-apis) with Freemium Catalog Discovery and x402 Solana USDC integration.

### Enterprise B2B Value Proposition (B2B Regulatory, KYB, FinTech & SecOps MCP Server (30 Tools))
- **Target B2B Buyers:** AI Agent Builders, Enterprise LLM Orchestration Teams, and Multi-Agent FinTech/SecOps Platforms.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`MCP Master Router Tool Discovery or Dispatch Executed`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~b2b-quant-mcp-server/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Artificial Intelligence/Machine Learning` | Zyla API Hub `AI & Machine Learning`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** mcp-server, model-context-protocol, ai-agent-tools, b2b-compliance-suite, claude-cursor-tools, langchain-b2b, autonomous-agents.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `operationMode` | `string` | Required | Select 'list_catalog' for free instant JSON-RPC 2.0 tools/list discovery of all 30 B2B tools, 'invoke_tool' to dispatch/validate a specific B2B tool call, or 'export_mcp_config' to generate ready-to-paste Claude Desktop, Cursor, Windsurf, and x402 configs. |
| `toolName` | `string` | Optional | Slug or MCP tool name of any of the 30 underlying @b2b-quant-apis engines (e.g., 'us-sec-edgar-filings-insider-radar', 'global-sanctions-pep-interpol-watchlist-screener', 'brazil-b2b-cnpj-qsa-lead-enricher'). |
| `toolArguments` | `object` | Optional | Structured JSON arguments passed to the target B2B tool when operationMode is 'invoke_tool'. |
| `categoryFilter` | `string` | Optional | Filter the 30 B2B tools by domain category in 'list_catalog' mode ('ALL', 'FINANCE_KYB', 'GOVCON_PROCUREMENT', 'SECOPS_CYBER', 'HEALTHCARE_BIOTECH', 'BRAZIL_B2B_TAX', or 'ESG_LOGISTICS_GEO'). |
| `apifyApiToken` | `string` | Optional | Optional Apify API Token to execute a live synchronous REST call against the target @b2b-quant-apis Actor during 'invoke_tool'. If omitted, returns a deterministic validated MCP execution envelope. |
| `maxTools` | `integer` | Optional | Maximum number of B2B tool definitions to return in 'list_catalog' mode (1 to 30). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `operationMode` | `string` | Executed router mode: list_catalog, invoke_tool, or export_mcp_config. |
| `toolName` | `string` | Canonical MCP tool identifier (underscore format). |
| `actorSlug` | `string` | Full @b2b-quant-apis Actor slug on Apify Store. |
| `domainCategory` | `string` | Classified vertical category (FINANCE_KYB, GOVCON_PROCUREMENT, SECOPS_CYBER, etc.). |
| `pricePerEventUsd` | `number` | Pay-Per-Event price in USD on Apify Store and x402 Solana USDC gateway. |
| `mcpStreamableHttpUrl` | `string` | Direct Hosted Apify MCP Server URL for this tool. |
| `x402SolanaEndpoint` | `string` | Stateless x402 endpoint settling in USDC on Solana Mainnet. |
| `executionStatus` | `string` | READY_IN_CATALOG, LIVE_DISPATCH_SUCCEEDED, DETERMINISTIC_VALIDATED_ENVELOPE, or CONFIG_EXPORTED. |
| `readinessScore` | `integer` | Quantitative schema, MCP, and x402 readiness score (0-100). |
| `mcpJsonRpcEnvelope` | `object` | Complete JSON-RPC 2.0 tools/list, tools/call, or configuration payload. |
| `markdownMcpBrief` | `string` | Executive Markdown documentation and 1-Click setup snippet for AI Agents. |
| `dispatchedItemCount` | `integer` | dispatchedItemCount validated by B2B Regulatory, KYB, FinTech & SecOps MCP Server (30 Tools). |

## Verified Authentic Response Example
```json
{
  "operationMode": "invoke_tool",
  "toolName": "us_sec_edgar_filings_insider_radar",
  "domainCategory": "FINTECH_SEC_TAX",
  "executionStatus": "LIVE_DISPATCH_SUCCEEDED",
  "readinessScore": 99,
  "dispatchedItemCount": 1,
  "mcpJsonRpcEnvelope": {
    "jsonrpc": "2.0",
    "id": "tools-call-us-sec-edgar-filings-insider-radar",
    "method": "tools/call",
    "result": {
      "protocolVersion": "2025-03-26",
      "toolName": "us_sec_edgar_filings_insider_radar",
      "isError": false,
      "structuredContent": [
        {
          "accessionNumber": "0000320193-26-000026",
          "cik": "0000320193",
          "ticker": "AAPL",
          "companyName": "Apple Inc.",
          "formType": "10-K",
          "filingDate": "2026-11-03",
          "reportDate": "2026-09-26",
          "governanceAlertScore": 84,
          "itemsSummary": "10-K",
          "edgarDocumentUrl": "https://www.sec.gov/Archives/edgar/data/320193/000032019326000026/aapl-20260926.htm",
          "markdownGovernanceBrief": "# SEC EDGAR GOVERNANCE & COMPLIANCE BRIEF: AAPL (10-K)\n\n## 1. Registrant & Filing Identification\n- **Company Name:** Apple Inc.\n- **Ticker / CIK:** `AAPL` / `0000320193`\n- **Accession Number:** `0000320193-26-000026`\n- **Form Type:** `10-K` (STANDARD STATUTORY DISCLOSURE)\n- **Governance Alert Score:** **84/100**\n\n## 2. Regulatory Timeline & Disclosure Scope\n- **SEC Filing Date:** 2026-11-03\n- **Period of Report:** 2026-09-26\n- **Material Items / Primary Description:** 10-K\n- **Official SEC EDGAR Archive URL:** https://www.sec.gov/Archives/edgar/data/320193/000032019326000026/aapl-20260926.htm"
        }
      ]
    }
  },
  "markdownMcpBrief": "# B2B REGULATORY & COMPLIANCE MCP ROUTER BRIEF: `us_sec_edgar_filings_insider_radar`\n\n- **Operation Mode:** `invoke_tool`\n- **Dispatched Domain Engine:** `us_sec_edgar_filings_insider_radar` (`FINTECH_SEC_TAX`)\n- **Execution Status:** `LIVE_DISPATCH_SUCCEEDED` (1 structured record returned)\n- **Readiness Score:** 99/100"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-quant-mcp-server/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "operationMode": "list_catalog",
  "toolName": "us-sec-edgar-filings-insider-radar",
  "toolArguments": {
    "tickers": [
      "AAPL",
      "NVDA"
    ],
    "form_types": [
      "10-K",
      "8-K"
    ],
    "max_filings_per_company": 3
  },
  "categoryFilter": "ALL",
  "maxTools": 30
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-quant-mcp-server/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"operationMode": "list_catalog", "toolName": "us-sec-edgar-filings-insider-radar", "toolArguments": {"tickers": ["AAPL", "NVDA"], "form_types": ["10-K", "8-K"], "max_filings_per_company": 3}, "categoryFilter": "ALL", "maxTools": 30}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
