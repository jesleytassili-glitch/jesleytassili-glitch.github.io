# UK Corporate Entity GLEIF LEI & Company Number Verifier

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/uk-fca-companies-house-kyb-compliance-auditor.html](https://jesleytassili-glitch.github.io/docs/uk-fca-companies-house-kyb-compliance-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/uk-fca-companies-house-kyb-compliance-auditor.md](https://jesleytassili-glitch.github.io/docs/uk-fca-companies-house-kyb-compliance-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/uk-fca-companies-house-kyb-compliance-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/uk-fca-companies-house-kyb-compliance-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/uk-fca-companies-house-kyb-compliance-auditor](https://apify.com/b2b-quant-apis/uk-fca-companies-house-kyb-compliance-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/uk+fca+companies+house+kyb+compliance+api/14660](https://zylalabs.com/api-marketplace/legal+%26+compliance/uk+fca+companies+house+kyb+compliance+api/14660)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Verifies UK legal entities in the official GLEIF LEI registry: legal name, Companies House registration number, LEI, entity status, creation date, registered city/postcode and LEI renewal. No FCA or SIC data. No scoring.

### Enterprise B2B Value Proposition (UK Corporate Entity GLEIF LEI & Company Number Verifier)
- **Target B2B Buyers:** UK/EU FinTechs, Commercial Banks, Legal Conveyancing Platforms, and Vendor Onboarding Systems.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Official Registry Attributes & RAG Briefs:** Every record provides verified GLEIF LEI status, Companies House CRN, incorporation date, registered city/postcode, and an LLM-ready Markdown KYB dossier (no FCA licensing data, SIC codes, or synthetic scoring).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~uk-fca-companies-house-kyb-compliance-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** uk-companies-house, crn-lookup, uk-kyb-verification, lei-entity-status, british-corporate-registry, gleif-uk, aml-due-diligence.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `companyQuery` | `string` | Required | United Kingdom legal entity name or 8-character Companies House Registration Number (e.g., 'Revolut', 'Barclays', 'Wise', 'Monzo', '08804411'). |
| `includeInactive` | `boolean` | Optional | If true, includes dissolved, liquidated, or lapsed UK entities alongside active companies. |
| `maxResults` | `integer` | Optional | Maximum number of UK corporate entity records to extract (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `companyNumberCrn` | `string` | Company registration number reported in the GLEIF registry (8 characters for Companies House). |
| `companyName` | `string` | Official legal name registered in GLEIF. |
| `leiCode` | `string` | ISO 17442 Legal Entity Identifier. |
| `companyStatus` | `string` | GLEIF entity status (ACTIVE or INACTIVE). |
| `incorporationDate` | `string` | ISO date of entity creation reported by GLEIF. |
| `registeredCity` | `string` | City of the legal address. |
| `registeredPostalCode` | `string` | Postcode of the legal address. |
| `leiRegistrationStatus` | `string` | ISSUED, LAPSED, RETIRED, etc. |
| `leiNextRenewalDate` | `string` | ISO date when the LEI must next be renewed. |
| `registrationAuthorityId` | `string` | GLEIF registration authority code (RA000585 = Companies House). |
| `markdownKybBrief` | `string` | Executive Markdown dossier built only from GLEIF registry fields. |

## Verified Authentic Response Example
```json
{
  "companyNumberCrn": "12871051",
  "companyName": "REVOLUT BANK UK LTD",
  "leiCode": "2138003LXONKR247S255",
  "companyStatus": "ACTIVE",
  "incorporationDate": "2020-09-10",
  "registeredCity": "LONDON",
  "registeredPostalCode": "E14 5AB",
  "leiRegistrationStatus": "ISSUED",
  "leiNextRenewalDate": "2026-12-08",
  "registrationAuthorityId": "RA000585",
  "markdownKybBrief": "# UK CORPORATE ENTITY GLEIF LEI DOSSIER: 12871051\n\n## 1. Corporate Registry & Legal Identity\n- **Legal Entity Name:** **REVOLUT BANK UK LTD**\n- **UK Companies House CRN:** `12871051`\n- **GLEIF 20-Character LEI:** `2138003LXONKR247S255`\n- **Registration Authority ID:** `RA000585`\n- **Entity Operational Status:** `ACTIVE`\n- **Incorporation Date:** `2020-09-10`\n\n## 2. Registered Office & LEI Lifecycle\n- **Registered City / Postcode:** `LONDON, E14 5AB`\n- **LEI Registration Status:** `ISSUED`\n- **LEI Next Renewal Date:** `2026-12-08`"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~uk-fca-companies-house-kyb-compliance-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "companyQuery": "Revolut",
  "includeInactive": false,
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~uk-fca-companies-house-kyb-compliance-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"companyQuery": "Revolut", "includeInactive": false, "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
