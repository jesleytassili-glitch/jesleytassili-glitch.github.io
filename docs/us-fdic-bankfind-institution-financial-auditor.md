# US FDIC BankFind Institution & Solvency Risk Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-fdic-bankfind-institution-financial-auditor.html](https://jesleytassili-glitch.github.io/docs/us-fdic-bankfind-institution-financial-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-fdic-bankfind-institution-financial-auditor.md](https://jesleytassili-glitch.github.io/docs/us-fdic-bankfind-institution-financial-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-fdic-bankfind-institution-financial-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-fdic-bankfind-institution-financial-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-fdic-bankfind-institution-financial-auditor](https://apify.com/b2b-quant-apis/us-fdic-bankfind-institution-financial-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/finance+%26+payments/us+fdic+bankfind+institution+financial+api/14656](https://zylalabs.com/api-marketplace/finance+%26+payments/us+fdic+bankfind+institution+financial+api/14656)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Audits U.S. FDIC-insured commercial banks and savings institutions via the official FDIC BankFind Suite API. Extracts total assets, deposits, equity capital, ROA, ROE, and calculates counterparty solvency health scores (0-100) for corporate treasury teams.

### Enterprise B2B Value Proposition (US FDIC BankFind Institution & Solvency Risk Auditor)
- **Target B2B Buyers:** Corporate Treasurers, CFOs, Institutional Counterparty Risk Teams, and FinTech Payment Routers.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`FDIC Insured Bank Solvency & Treasury Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-fdic-bankfind-institution-financial-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Finance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** fdic-bankfind, bank-solvency, treasury-risk, tier1-capital, banking-kyb, counterparty-risk, us-banks.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `institutionName` | `string` | Optional | Optional bank name keyword (e.g., 'JPMorgan', 'Citibank', 'Morgan Stanley', 'Bank of America'). |
| `state` | `string` | Optional | 2-letter US State code of bank headquarters (e.g., 'NY', 'CA', 'TX', 'OH', 'NC', 'SD'). |
| `activeOnly` | `boolean` | Optional | Filter exclusively for currently active FDIC-insured banks (ACTIVE=1). |
| `maxResults` | `integer` | Optional | Maximum number of FDIC institutions to extract and score (1 to 200). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `certNumber` | `string` | Official unique FDIC Certificate Number. |
| `institutionName` | `string` | Official legal name of the banking institution. |
| `city` | `string` | City of headquarters. |
| `state` | `string` | 2-letter US State abbreviation. |
| `activeStatus` | `boolean` | True if currently active and insured by the FDIC. |
| `totalAssetsMillionsUsd` | `number` | Total consolidated assets reported in millions of USD. |
| `totalDepositsMillionsUsd` | `number` | Total domestic and foreign deposits in millions of USD. |
| `equityRatioPct` | `number` | Tier/Book Equity capital as a percentage of total assets. |
| `roaPct` | `number` | Net income as a percentage of average total assets. |
| `counterpartyHealthScore` | `integer` | Quantitative treasury solvency & capital adequacy score (0-100). |
| `markdownTreasuryRiskBrief` | `string` | Executive Markdown dossier for CFOs, Corporate Treasurers, and Fintech Risk Teams. |
| `regulator` | `string` | regulator returned by US FDIC BankFind Institution & Solvency Risk Auditor. |

## Verified Authentic Response Example
```json
{
  "certNumber": "628",
  "institutionName": "JPMorgan Chase Bank, National Association",
  "city": "Columbus",
  "state": "OH",
  "regulator": "OCC",
  "activeStatus": true,
  "totalAssetsMillionsUsd": 4091315.0,
  "totalDepositsMillionsUsd": 2820284.0,
  "equityRatioPct": 8.35,
  "roaPct": 1.59,
  "counterpartyHealthScore": 85,
  "markdownTreasuryRiskBrief": "# US FDIC TREASURY COUNTERPARTY SOLVENCY BRIEF: JPMorgan Chase Bank, National Association (CERT #628)\n\n## 1. Institution & Regulatory Identification\n- **Institution Legal Name:** JPMorgan Chase Bank, National Association\n- **FDIC Certificate Number:** `628`\n- **Headquarters:** Columbus, OH\n- **Primary Federal Regulator:** `OCC`\n- **FDIC Insurance Status:** ACTIVE (Insured)\n- **Counterparty Health Score:** **85/100** (TIER-1 STRONG SOLVENCY / APPROVED COUNTERPARTY)\n\n## 2. Balance Sheet & Capital Adequacy Metrics\n- **Total Consolidated Assets:** $4,091,315.00 Million USD\n- **Total Deposits:** $2,820,284.00 Million USD\n- **Equity-to-Assets Capital Ratio:** 8.35%\n- **Return on Assets (ROA):** 1.59%"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-fdic-bankfind-institution-financial-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "institutionName": "JPMorgan Chase Bank",
  "state": "NY",
  "activeOnly": true,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-fdic-bankfind-institution-financial-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"institutionName": "JPMorgan Chase Bank", "state": "NY", "activeOnly": true, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
