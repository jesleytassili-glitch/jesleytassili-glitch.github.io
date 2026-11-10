# US EPA ECHO Environmental Compliance & ESG Penalty Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-epa-echo-environmental-compliance-auditor.html](https://jesleytassili-glitch.github.io/docs/us-epa-echo-environmental-compliance-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-epa-echo-environmental-compliance-auditor.md](https://jesleytassili-glitch.github.io/docs/us-epa-echo-environmental-compliance-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-epa-echo-environmental-compliance-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-epa-echo-environmental-compliance-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-epa-echo-environmental-compliance-auditor](https://apify.com/b2b-quant-apis/us-epa-echo-environmental-compliance-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/us+epa+echo+environmental+compliance+api/14653](https://zylalabs.com/api-marketplace/legal+%26+compliance/us+epa+echo+environmental+compliance+api/14653)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Audits industrial facilities across the United States via the official U.S. EPA ECHO REST API. Extracts Clean Air/Water/RCRA non-compliance quarters, Significant Non-Complier (SNC) flags, and federal penalties to calculate ESG liability scores (0-100).

### Enterprise B2B Value Proposition (US EPA ECHO Environmental Compliance & ESG Penalty Auditor)
- **Target B2B Buyers:** ESG Rating Agencies, Institutional Investors, Environmental Law Firms, and Supply Chain Risk Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`EPA Industrial Facility ESG & Penalty Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-epa-echo-environmental-compliance-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Data` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** epa-echo, esg-compliance, environmental-risk, clean-air-water-act, rcra-hazmat, industrial-due-diligence, supply-chain-esg.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `state` | `string` | Required | 2-letter US State code where industrial facilities are located (e.g., 'TX', 'CA', 'LA', 'OH', 'PA'). |
| `facilityName` | `string` | Optional | Optional facility or operator name keyword (e.g., 'Refinery', 'Chemical', 'Plant', 'Energy'). |
| `zipCode` | `string` | Optional | Optional 5-digit US postal code to narrow environmental due diligence (e.g., '77506', '77002'). |
| `significantViolatorsOnly` | `boolean` | Optional | Filter exclusively for facilities currently in Significant Non-Compliance (SNC) under CAA, CWA, or RCRA. |
| `maxResults` | `integer` | Optional | Maximum number of EPA-regulated facilities to extract and score (1 to 200). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `registryId` | `string` | Official U.S. EPA Facility Registry Service (FRS) identifier. |
| `facilityName` | `string` | Regulated industrial plant or facility name. |
| `city` | `string` | City where the facility is located. |
| `state` | `string` | 2-letter US State code. |
| `complianceStatus` | `string` | Current compliance status across Clean Air, Clean Water, and RCRA statutes. |
| `sncFlag` | `boolean` | True if flagged as Significant Non-Complier or High Priority Violator. |
| `quartersInNonCompliance` | `integer` | Number of quarters (0 to 12) in non-compliance over the last 3 years. |
| `totalPenaltiesUsd` | `number` | Cumulative formal enforcement monetary penalties assessed in USD. |
| `environmentalLiabilityScore` | `integer` | Quantitative ESG and environmental liability risk score (0-100). |
| `inspectionCount5Yr` | `integer` | Total federal and state regulatory inspections conducted. |
| `markdownEsgDueDiligenceBrief` | `string` | Executive environmental liability dossier for commercial real estate, M&A, and ESG risk teams. |

## Verified Authentic Response Example
```json
{
  "registryId": "110000463178",
  "facilityName": "BAYTOWN OLEFINS PLANT",
  "city": "BAYTOWN",
  "state": "TX",
  "complianceStatus": "Significant Violation",
  "sncFlag": true,
  "quartersInNonCompliance": 12,
  "totalPenaltiesUsd": 2204913.0,
  "environmentalLiabilityScore": 100,
  "inspectionCount5Yr": 11,
  "markdownEsgDueDiligenceBrief": "# US EPA ECHO ENVIRONMENTAL & ESG DUE DILIGENCE BRIEF: 110000463178\n\n## 1. Facility Identification & Jurisdiction\n- **Facility Name:** BAYTOWN OLEFINS PLANT\n- **EPA FRS Registry ID:** `110000463178`\n- **Location:** BAYTOWN, TX\n- **Environmental Liability Score:** **100/100** (CRITICAL ENVIRONMENTAL LIABILITY (PHASE II ESA RECOMMENDED))\n\n## 2. Multi-Statute Compliance & Enforcement Profile (CAA / CWA / RCRA)\n- **Current Compliance Status:** Significant Violation\n- **Significant Non-Complier (SNC / HPV Flag):** YES (Active Alert)\n- **Quarters in Non-Compliance (3-Year Window):** 12 / 12 quarters\n- **Cumulative Monetary Penalties Assessed:** $2,204,913.00 USD\n- **Regulatory Inspections (5-Year Window):** 11"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-epa-echo-environmental-compliance-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "state": "TX",
  "facilityName": "ExxonMobil",
  "zipCode": "",
  "significantViolatorsOnly": false,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-epa-echo-environmental-compliance-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"state": "TX", "facilityName": "ExxonMobil", "zipCode": "", "significantViolatorsOnly": false, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
