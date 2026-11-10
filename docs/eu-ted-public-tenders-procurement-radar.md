# EU TED Public Tenders & B2G Procurement Intelligence Radar

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/eu-ted-public-tenders-procurement-radar.html](https://jesleytassili-glitch.github.io/docs/eu-ted-public-tenders-procurement-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/eu-ted-public-tenders-procurement-radar.md](https://jesleytassili-glitch.github.io/docs/eu-ted-public-tenders-procurement-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/eu-ted-public-tenders-procurement-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/eu-ted-public-tenders-procurement-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/eu-ted-public-tenders-procurement-radar](https://apify.com/b2b-quant-apis/eu-ted-public-tenders-procurement-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+ted+public+tenders+procurement+radar+api/14648](https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+ted+public+tenders+procurement+radar+api/14648)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/eu-ted-public-tenders-procurement-radar](https://rapidapi.com/b2bquantapis/api/eu-ted-public-tenders-procurement-radar)

## Executive Overview
Extracts and scores European Union public procurement notices and contract awards from the official EU TED (Tenders Electronic Daily) portal. Enriches CPV codes, contracting authorities, EUR contract values, deadlines, and Bid Opportunity Scores.

### Enterprise B2B Value Proposition (EU TED Public Tenders & B2G Procurement Intelligence Radar)
- **Target B2B Buyers:** European B2G Bid Teams, Multinational IT Integrators, and Global Public Procurement Aggregators.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`EU TED Public Procurement Notice Analyzed`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~eu-ted-public-tenders-procurement-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** eu-ted-tenders, european-procurement, cpv-codes, public-sector-bids, b2g-europe, official-journal-ojs, government-rfp.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `searchKeyword` | `string` | Required | Public tender topic, CPV keyword, or technology sector (e.g., 'Cloud Cybersecurity', 'Artificial Intelligence', 'Medical Devices', 'Solar Energy'). |
| `countryIso3` | `string` | Optional | Optional 3-letter ISO country code (e.g., 'DEU', 'FRA', 'ESP', 'ITA', 'NLD', 'BEL', or leave empty for all EU/EEA member states). |
| `maxResults` | `integer` | Optional | Maximum number of European public procurement notices to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `publicationNumber` | `string` | Official Supplement to the Official Journal of the EU (OJ S) notice ID. |
| `noticeTitle` | `string` | Official title of the public procurement notice. |
| `buyerName` | `string` | European ministry, agency, or public utility issuing the tender. |
| `buyerCountryIso3` | `string` | 3-letter ISO code of the contracting authority country. |
| `cpvCode` | `string` | 8-digit EU Common Procurement Vocabulary classification code. |
| `procedureType` | `string` | Open, Restricted, Competitive Dialogue, or Framework Agreement. |
| `publicationDate` | `string` | ISO date when the notice was published on EU TED. |
| `deadlineDate` | `string` | ISO deadline for submitting bids or requests to participate. |
| `estimatedValueEur` | `number` | Estimated or awarded contract value in Euros (EUR). |
| `bidOpportunityScore` | `integer` | Quantitative B2G capture score combining contract value, open procedure openness, and CPV match (0-100). |
| `markdownProcurementBrief` | `string` | Executive Markdown brief for European B2G capture teams and automated RFP pipelines. |

## Verified Authentic Response Example
```json
{
  "publicationNumber": "674231-2026",
  "noticeTitle": "Czechia – Security software package – SW pro SIEM",
  "buyerName": "Středisko společných činností AV ČR, v. v. i.",
  "buyerCountryIso3": "CZE",
  "cpvCode": "48730000",
  "procedureType": "Open Procedure",
  "publicationDate": "2026-10-01",
  "deadlineDate": "2026-11-04",
  "estimatedValueEur": 5300000,
  "bidOpportunityScore": 94,
  "markdownProcurementBrief": "# EU TED PUBLIC PROCUREMENT BRIEF: 674231-2026\n\n## 1. Contracting Authority & Notice Identity\n- **Publication Number (OJ S):** `674231-2026`\n- **Tender Title:** **Czechia – Security software package – SW pro SIEM**\n- **Contracting Authority:** Středisko společných činností AV ČR, v. v. i. (`CZE`)\n- **Primary CPV Classification:** `48730000`\n- **Procedure Type:** `Open Procedure`\n\n## 2. Financial Valuation, Timeline & B2G Capture Score\n- **Bid Opportunity Score:** **94/100**\n- **Estimated Contract Value:** **€5,300,000.00 EUR**\n- **Publication Date:** `2026-10-01`\n- **Submission Deadline:** **`2026-11-04`**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~eu-ted-public-tenders-procurement-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "searchKeyword": "Cloud Cybersecurity",
  "countryIso3": "DEU",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~eu-ted-public-tenders-procurement-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"searchKeyword": "Cloud Cybersecurity", "countryIso3": "DEU", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
