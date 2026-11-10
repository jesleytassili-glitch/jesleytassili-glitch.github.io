# Global OFAC & UN Sanctions Watchlist AML Screener

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/global-sanctions-pep-interpol-watchlist-screener.html](https://jesleytassili-glitch.github.io/docs/global-sanctions-pep-interpol-watchlist-screener.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/global-sanctions-pep-interpol-watchlist-screener.md](https://jesleytassili-glitch.github.io/docs/global-sanctions-pep-interpol-watchlist-screener.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/global-sanctions-pep-interpol-watchlist-screener.json](https://jesleytassili-glitch.github.io/specs_openapi_31/global-sanctions-pep-interpol-watchlist-screener.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/global-sanctions-pep-interpol-watchlist-screener](https://apify.com/b2b-quant-apis/global-sanctions-pep-interpol-watchlist-screener)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646](https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/global-sanctions-pep-interpol-watchlist-screener](https://rapidapi.com/b2bquantapis/api/global-sanctions-pep-interpol-watchlist-screener)

## Executive Overview
Screens individuals, companies, vessels and crypto counterparties against the official US OFAC SDN, OFAC Consolidated (Non-SDN) and UN Security Council lists, downloaded live. Fuzzy match + AML Risk Score (0-100). EU, UK and PEP lists are not covered.

### Enterprise B2B Value Proposition (Global OFAC & UN Sanctions Watchlist AML Screener)
- **Target B2B Buyers:** Crypto Exchanges, Cross-Border Payment Gateways, Neobanks, and AML/KYC Compliance Officers.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Global OFAC / UN / EU Sanctions & PEP Entity Screened`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~global-sanctions-pep-interpol-watchlist-screener/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Cybersecurity` | Zyla API Hub `Security`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** ofac-sdn-sanctions, aml-kyc-screening, pep-watchlist, eu-un-sanctions, financial-crime-compliance, entity-screening, regtech-aml.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `entityName` | `string` | Required | Organization, vessel, or individual name to screen for AML/KYC compliance (e.g., 'Lazarus Group', 'Garantex', 'Rosneft', 'Wagner'). |
| `entityType` | `string` | Optional | Filter by 'ANY', 'ORGANIZATION', 'INDIVIDUAL', or 'VESSEL'. |
| `maxResults` | `integer` | Optional | Maximum number of sanctions watchlist hits to return and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `watchlistRecordId` | `string` | Official OFAC / UN list identifier. |
| `entityQuery` | `string` | Input name submitted for AML/KYC screening. |
| `matchedName` | `string` | Official designated name on the OFAC or UN sanctions list. |
| `entityType` | `string` | ORGANIZATION, INDIVIDUAL, or VESSEL. |
| `listSource` | `string` | US OFAC SDN, US OFAC Consolidated (Non-SDN) or UN Security Council. |
| `sanctionsProgram` | `string` | Specific regulatory program (e.g., CYBER2, DPRK3, RUSSIA-EO14024). |
| `jurisdiction` | `string` | 2-letter ISO country code associated with the designated entity. |
| `matchSimilarityScore` | `integer` | Token and Jaro-Winkler lexical similarity score (0-100). |
| `amlRiskScore` | `integer` | Composite AML/CFT risk score (0-100). |
| `screeningDecision` | `string` | BLOCK_SANCTIONED, ESCALATE_COMPLIANCE_REVIEW, or CLEAR_NO_HIT. |
| `markdownAmlBrief` | `string` | Executive Markdown AML/KYC audit trail for compliance officers and automated onboarding. |

## Verified Authentic Response Example
```json
{
  "watchlistRecordId": "OFAC-SDN-27307",
  "entityQuery": "Lazarus Group",
  "matchedName": "LAZARUS GROUP",
  "entityType": "ORGANIZATION",
  "listSource": "US OFAC SDN & UN Security Council",
  "sanctionsProgram": "DPRK3 / CYBER2",
  "jurisdiction": "KP",
  "matchSimilarityScore": 100,
  "amlRiskScore": 100,
  "screeningDecision": "BLOCK_SANCTIONED",
  "markdownAmlBrief": "# GLOBAL AML & SANCTIONS WATCHLIST SCREENING DOSSIER: OFAC-SDN-27307\n\n## 1. Screened Counterparty & Watchlist Match\n- **Screened Query:** `Lazarus Group`\n- **Matched Watchlist Entity:** **LAZARUS GROUP**\n- **Entity Type:** `ORGANIZATION`\n- **Watchlist Authority / Source:** US OFAC SDN & UN Security Council\n- **Sanctions Program / Designation:** `DPRK3 / CYBER2`\n- **Jurisdiction ISO:** `KP`\n\n## 2. Quantitative AML Risk & Compliance Decision\n- **Lexical Similarity Score:** `100/100`\n- **Composite AML Risk Score:** **100/100**\n- **Automated Compliance Decision:** **`BLOCK_SANCTIONED`**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~global-sanctions-pep-interpol-watchlist-screener/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "entityName": "Lazarus Group",
  "entityType": "ANY",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~global-sanctions-pep-interpol-watchlist-screener/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"entityName": "Lazarus Group", "entityType": "ANY", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
