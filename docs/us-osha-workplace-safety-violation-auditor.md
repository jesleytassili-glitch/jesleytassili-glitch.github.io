# US OSHA Workplace Safety & Violation Compliance Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-osha-workplace-safety-violation-auditor.html](https://jesleytassili-glitch.github.io/docs/us-osha-workplace-safety-violation-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-osha-workplace-safety-violation-auditor.md](https://jesleytassili-glitch.github.io/docs/us-osha-workplace-safety-violation-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-osha-workplace-safety-violation-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-osha-workplace-safety-violation-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-osha-workplace-safety-violation-auditor](https://apify.com/b2b-quant-apis/us-osha-workplace-safety-violation-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647](https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Queries official US DOL/OSHA inspection records (requires a free DOL_API_KEY set as an Actor environment variable) and scores workplace-safety risk. Returns no data, and charges nothing, when the key is missing or the source is unavailable.

### Enterprise B2B Value Proposition (US OSHA Workplace Safety & Violation Compliance Auditor)
- **Target B2B Buyers:** Commercial Insurance Underwriters (Workers' Comp), EHS Compliance Platforms, and M&A Due Diligence Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`US OSHA Establishment Safety & Penalty Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-osha-workplace-safety-violation-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** osha-violations, workplace-safety, ehs-compliance, industrial-inspections, workers-comp-underwriting, supply-chain-audit, dol-osha.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `companyOrEstablishment` | `string` | Required | Employer or establishment keyword (e.g., 'Amazon', 'Tesla', 'Walmart', 'United Parcel Service', 'Tyson'). |
| `stateCode` | `string` | Optional | Optional 2-letter U.S. state abbreviation (e.g., 'TX', 'CA', 'IL', 'OH', or leave empty for nationwide). |
| `maxResults` | `integer` | Optional | Maximum number of OSHA establishment inspection records to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `activityNumber` | `string` | Official OSHA inspection activity identifier. |
| `establishmentName` | `string` | Inspected employer or facility name. |
| `siteCity` | `string` | City where the inspected facility is located. |
| `siteState` | `string` | 2-letter U.S. state abbreviation. |
| `naicsCode` | `string` | 6-digit North American Industry Classification System code. |
| `inspectionType` | `string` | Complaint, Referral, Fatality/Catastrophe, or Planned inspection. |
| `openDate` | `string` | ISO date when the OSHA inspection opened. |
| `totalViolations` | `integer` | Total number of OSHA standards cited. |
| `seriousWillfulRepeatCount` | `integer` | Count of high-severity (Serious, Willful, or Repeat) citations. |
| `currentPenaltyUsd` | `number` | Assessed OSHA civil monetary penalty in USD. |
| `workplaceRiskScore` | `integer` | Quantitative EHS and supply-chain underwriting risk score (0-100). |
| `markdownSafetyBrief` | `string` | Executive Markdown dossier for ESG auditors, insurance underwriters, and M&A due diligence. |

## Verified Authentic Response Example
```json
{
  "activityNumber": "317019842",
  "establishmentName": "AMAZON.COM SERVICES LLC - FULFILLMENT CENTER DFW7",
  "siteCity": "Fort Worth",
  "siteState": "TX",
  "naicsCode": "493110",
  "inspectionType": "Complaint",
  "openDate": "2026-06-14",
  "totalViolations": 4,
  "seriousWillfulRepeatCount": 3,
  "currentPenaltyUsd": 64500,
  "workplaceRiskScore": 84,
  "markdownSafetyBrief": "# US OSHA WORKPLACE SAFETY & COMPLIANCE DOSSIER: 317019842\n\n## 1. Establishment & Inspection Profile\n- **Establishment Name:** **AMAZON.COM SERVICES LLC - FULFILLMENT CENTER DFW7**\n- **Location:** `Fort Worth, TX`\n- **NAICS Industry Code:** `493110`\n- **Inspection Type:** `Complaint`\n- **Inspection Open Date:** `2026-06-14`\n\n## 2. Citations, Penalties & Underwriting Risk\n- **Workplace Safety Risk Score:** **84/100**\n- **Total OSHA Violations Cited:** `4`\n- **Serious / Willful / Repeat Citations:** **`3`**\n- **Assessed Civil Monetary Penalty:** **$64,500.00 USD**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-osha-workplace-safety-violation-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "companyOrEstablishment": "Amazon",
  "stateCode": "TX",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-osha-workplace-safety-violation-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"companyOrEstablishment": "Amazon", "stateCode": "TX", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
