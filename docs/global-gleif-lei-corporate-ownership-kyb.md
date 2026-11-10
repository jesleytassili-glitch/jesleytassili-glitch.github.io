# Global GLEIF LEI Corporate Ownership & KYB Compliance Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/global-gleif-lei-corporate-ownership-kyb.html](https://jesleytassili-glitch.github.io/docs/global-gleif-lei-corporate-ownership-kyb.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/global-gleif-lei-corporate-ownership-kyb.md](https://jesleytassili-glitch.github.io/docs/global-gleif-lei-corporate-ownership-kyb.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/global-gleif-lei-corporate-ownership-kyb.json](https://jesleytassili-glitch.github.io/specs_openapi_31/global-gleif-lei-corporate-ownership-kyb.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/global-gleif-lei-corporate-ownership-kyb](https://apify.com/b2b-quant-apis/global-gleif-lei-corporate-ownership-kyb)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/global+gleif+lei+corporate+ownership+kyb+api/14657](https://zylalabs.com/api-marketplace/legal+%26+compliance/global+gleif+lei+corporate+ownership+kyb+api/14657)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/global-gleif-lei-corporate-ownership-kyb](https://rapidapi.com/b2bquantapis/api/global-gleif-lei-corporate-ownership-kyb)

## Executive Overview
Audits multinational corporate entities via the official GLEIF LEI API v1 (Zero-Key, 2.5M+ companies). Extracts 20-char LEI codes, legal jurisdiction, registration status, headquarters, and calculates KYB Trust Scores (0-100).

### Enterprise B2B Value Proposition (Global GLEIF LEI Corporate Ownership & KYB Compliance Auditor)
- **Target B2B Buyers:** Global Investment Banks, RegTech KYB Platforms, Crypto Institutional Desks, and Trade Finance Systems.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Global GLEIF LEI Corporate Entity Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~global-gleif-lei-corporate-ownership-kyb/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** gleif-lei, legal-entity-identifier, global-kyb, corporate-ownership, mifid-ii-emir, parent-subsidiary, aml-onboarding.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `companyName` | `string` | Required | Corporate legal name to search in the Global LEI Index (e.g., 'Microsoft', 'Siemens', 'JPMorgan', 'Petrobras'). |
| `countryCode` | `string` | Optional | Optional 2-letter ISO country filter (e.g., 'US', 'DE', 'GB', 'BR'). |
| `maxResults` | `integer` | Optional | Maximum number of GLEIF LEI records to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `leiCode` | `string` | ISO 17442 Global Legal Entity Identifier. |
| `legalName` | `string` | Registered legal name of the entity. |
| `jurisdiction` | `string` | ISO country/subdivision of legal formation. |
| `entityStatus` | `string` | ACTIVE or INACTIVE legal entity status. |
| `registrationStatus` | `string` | ISSUED, LAPSED, RETIRED, or ANNULLED. |
| `registeredAs` | `string` | Local commercial register number. |
| `headquartersCity` | `string` | City of corporate headquarters. |
| `headquartersCountry` | `string` | ISO country code of headquarters. |
| `nextRenewalDate` | `string` | Scheduled annual LEI renewal timestamp. |
| `kybTrustScore` | `integer` | Quantitative KYB compliance and registration validity score (0-100). |
| `markdownKybBrief` | `string` | Executive KYB audit dossier for banking, M&A, and vendor onboarding. |

## Verified Authentic Response Example
```json
{
  "leiCode": "INR2EJN1ERAN0W5ZP974",
  "legalName": "MICROSOFT CORPORATION",
  "jurisdiction": "US-WA",
  "entityStatus": "ACTIVE",
  "registrationStatus": "ISSUED",
  "registeredAs": "600 413 485",
  "headquartersCity": "REDMOND",
  "headquartersCountry": "US",
  "nextRenewalDate": "2027-05-04T00:00:00Z",
  "kybTrustScore": 100,
  "markdownKybBrief": "# GLOBAL GLEIF LEI CORPORATE KYB AUDIT: MICROSOFT CORPORATION\n\n## 1. ISO 17442 LEI & Legal Identity\n- **20-Character LEI Code:** `INR2EJN1ERAN0W5ZP974`\n- **Official Legal Name:** **MICROSOFT CORPORATION**\n- **Legal Jurisdiction:** `US-WA`\n- **Local Commercial Registry ID:** `600 413 485`\n\n## 2. Regulatory Status & Headquarters\n- **Entity Operational Status:** `ACTIVE`\n- **LEI Registration Status:** `ISSUED`\n- **Headquarters Location:** REDMOND, US\n- **Next Annual Renewal Date:** 2027-05-04T00:00:00Z\n- **KYB Compliance Trust Score:** **100/100**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~global-gleif-lei-corporate-ownership-kyb/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "companyName": "Microsoft",
  "countryCode": "US",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~global-gleif-lei-corporate-ownership-kyb/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"companyName": "Microsoft", "countryCode": "US", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
