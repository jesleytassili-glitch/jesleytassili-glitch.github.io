# US Federal Contracts & SAM.gov Procurement B2G Radar

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-sam-gov-federal-procurement-auditor.html](https://jesleytassili-glitch.github.io/docs/us-sam-gov-federal-procurement-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-sam-gov-federal-procurement-auditor.md](https://jesleytassili-glitch.github.io/docs/us-sam-gov-federal-procurement-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-sam-gov-federal-procurement-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-sam-gov-federal-procurement-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-sam-gov-federal-procurement-auditor](https://apify.com/b2b-quant-apis/us-sam-gov-federal-procurement-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647](https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Extracts and audits official U.S. Federal Government contract awards via USAspending.gov v2 and SAM.gov APIs (Zero-Key required). Scores B2G vendor competitiveness (0-100), tracks DoD/HHS/VA awards, and generates Markdown procurement briefs.

### Enterprise B2B Value Proposition (US Federal Contracts & SAM.gov Procurement B2G Radar)
- **Target B2B Buyers:** U.S. Federal Defense Contractors, GovCon BD Teams, and Public Sector Market Intelligence Platforms.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`U.S. Federal Contract Award & B2G Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-sam-gov-federal-procurement-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** sam-gov, usaspending, federal-contracts, govcon-intelligence, naics-psc, b2g-procurement, defense-contracts.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `keyword` | `string` | Required | Keyword searched in federal contract award descriptions (e.g., 'cybersecurity', 'cloud software', 'medical supplies', 'autonomous'). |
| `awardingAgency` | `string` | Optional | Optional filter by top-tier U.S. Federal Agency name (e.g., 'Department of Defense', 'Department of Veterans Affairs'). |
| `minAwardAmount` | `integer` | Optional | Minimum contract obligation amount in USD (0 to 1,000,000,000). |
| `maxResults` | `integer` | Optional | Maximum number of federal contract awards to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `awardId` | `string` | Official Procurement Instrument Identifier (PIID). |
| `recipientName` | `string` | Legal entity awarded the federal contract. |
| `awardingAgency` | `string` | Top-tier U.S. Federal Department or Agency. |
| `awardingSubAgency` | `string` | Specific bureau, command, or sub-agency. |
| `awardAmountUsd` | `number` | Total federal contract award amount in USD. |
| `startDate` | `string` | Contract period of performance start date (YYYY-MM-DD). |
| `endDate` | `string` | Contract period of performance end/renewal date (YYYY-MM-DD). |
| `contractAwardType` | `string` | Federal procurement instrument type (Definitive Contract, Delivery Order, BPA Call, Purchase Order). |
| `b2gOpportunityScore` | `integer` | Quantitative score evaluating contract value, recompete window, and B2G subcontracting potential (0-100). |
| `description` | `string` | Official summary of goods or services procured. |
| `markdownProcurementBrief` | `string` | Executive Markdown dossier for GovCon capture teams, B2B sales, and AI RAG agents. |

## Verified Authentic Response Example
```json
{
  "awardId": "FA862118F6251",
  "recipientName": "LOCKHEED MARTIN CORPORATION",
  "awardingAgency": "Department of Defense",
  "awardingSubAgency": "Department of the Air Force",
  "awardAmountUsd": 666315748.84,
  "startDate": "2018-02-08",
  "endDate": "2027-01-31",
  "contractAwardType": "DELIVERY ORDER",
  "b2gOpportunityScore": 100,
  "description": "IGF::OT::IGF  AFSOC ACTS AWARD OF CONTRACT FOR CLS, ENGINEERING, INSTRUCTION, CYBERSECURITY, DMO",
  "markdownProcurementBrief": "# US FEDERAL PROCUREMENT & SAM.GOV B2G BRIEF: FA862118F6251\n\n## 1. Award & Prime Contractor Summary\n- **Federal Award ID (PIID):** `FA862118F6251`\n- **Winning Prime Contractor:** LOCKHEED MARTIN CORPORATION\n- **Contract Obligation Value:** **$666,315,748.84 USD**\n- **B2G Opportunity Score:** **100/100** (PRIME SUBCONTRACTING & RECOMPETE TARGET)\n\n## 2. Federal Agency & Performance Timeline\n- **Awarding Agency:** Department of Defense\n- **Awarding Sub-Agency / Command:** Department of the Air Force\n- **Contract Instrument Type:** DELIVERY ORDER\n- **Period of Performance:** 2018-02-08 to 2027-01-31\n\n## 3. Scope of Work & Requirement Description\n- **Official Award Description:** IGF::OT::IGF  AFSOC ACTS AWARD OF CONTRACT FOR CLS, ENGINEERING, INSTRUCTION, CYBERSECURITY, DMO"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-sam-gov-federal-procurement-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "keyword": "cybersecurity",
  "awardingAgency": "",
  "minAwardAmount": 50000,
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-sam-gov-federal-procurement-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"keyword": "cybersecurity", "awardingAgency": "", "minAwardAmount": 50000, "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
