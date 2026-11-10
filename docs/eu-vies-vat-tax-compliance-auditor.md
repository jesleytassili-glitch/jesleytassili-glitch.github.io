# EU VIES VAT Number Validator & Reverse Charge Tax Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/eu-vies-vat-tax-compliance-auditor.html](https://jesleytassili-glitch.github.io/docs/eu-vies-vat-tax-compliance-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/eu-vies-vat-tax-compliance-auditor.md](https://jesleytassili-glitch.github.io/docs/eu-vies-vat-tax-compliance-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/eu-vies-vat-tax-compliance-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/eu-vies-vat-tax-compliance-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/eu-vies-vat-tax-compliance-auditor](https://apify.com/b2b-quant-apis/eu-vies-vat-tax-compliance-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+vies+vat+tax+compliance+auditor+api/14654](https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+vies+vat+tax+compliance+auditor+api/14654)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/eu-vies-vat-tax-compliance-auditor](https://rapidapi.com/b2bquantapis/api/eu-vies-vat-tax-compliance-auditor)

## Executive Overview
Validates European Union & Northern Ireland (XI) corporate VAT numbers in real time via the official EU Commission VIES REST API and local regex checksums. Audits Intra-EU Reverse Charge eligibility and generates Markdown compliance certificates.

### Enterprise B2B Value Proposition (EU VIES VAT Number Validator & Reverse Charge Tax Auditor)
- **Target B2B Buyers:** European B2B SaaS Billing Engines, Cross-Border Marketplaces, and ERP Tax Compliance Modules.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`EU VIES VAT & Reverse Charge Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~eu-vies-vat-tax-compliance-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Taxes & Compliance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** eu-vat-validation, vies-api, reverse-charge, cross-border-tax, european-kyb, vat-compliance, b2b-invoicing.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `vatNumbers` | `string` | Required | Comma, space, or newline-separated EU VAT numbers including 2-letter country prefix (e.g., 'IE6388047V, DE811128135, FR40303265045'). |
| `requesterCountryCode` | `string` | Optional | 2-letter EU country code of the invoicing entity (e.g., 'DE', 'NL', 'FR', 'IE') to determine Cross-Border B2B Reverse Charge (0% VAT) vs. Domestic VAT. |
| `maxResults` | `integer` | Optional | Maximum number of VAT records to audit in a single batch (1 to 200). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `fullVatNumber` | `string` | Normalized EU VAT identifier including Member State prefix. |
| `countryCode` | `string` | 2-letter EU VIES jurisdiction code (AT, BE, DE, EL, ES, FR, IE, IT, NL, XI, etc.). |
| `vatNumber` | `string` | National numeric/alphanumeric VAT digits without country prefix. |
| `syntaxValid` | `boolean` | Whether the VAT number matches the official Member State structural regex. |
| `viesActive` | `boolean` | Whether the VAT number is actively registered for Intra-EU cross-border transactions. |
| `traderName` | `string` | Legal company name returned by the European Commission VIES registry. |
| `traderAddress` | `string` | Official corporate address on file in the Member State tax registry. |
| `reverseChargeStatus` | `string` | Tax invoicing determination (ELIGIBLE_INTRA_EU_0_VAT, DOMESTIC_STANDARD_VAT, or DO_NOT_ZERO_RATE). |
| `complianceRiskScore` | `integer` | Quantitative tax audit risk score (0 = lowest risk/verified active, 100 = invalid/high risk). |
| `verificationSource` | `string` | Indicates EU_VIES_LIVE_API or ALGORITHMIC_FALLBACK_MS_MAINTENANCE. |
| `markdownVatCertificate` | `string` | Audit-ready Markdown VAT compliance certificate for ERP/Finance attachment. |
| `requesterCountryCode` | `string` | requesterCountryCode returned by EU VIES VAT Number Validator & Reverse Charge Tax Auditor. |

## Verified Authentic Response Example
```json
{
  "fullVatNumber": "IE6388047V",
  "countryCode": "IE",
  "vatNumber": "6388047V",
  "requesterCountryCode": "DE",
  "syntaxValid": true,
  "viesActive": true,
  "traderName": "GOOGLE IRELAND LIMITED",
  "traderAddress": "3RD FLOOR, GORDON HOUSE, BARROW STREET, DUBLIN 4",
  "reverseChargeStatus": "ELIGIBLE_INTRA_EU_0_VAT_REVERSE_CHARGE",
  "complianceRiskScore": 5,
  "verificationSource": "EU_VIES_LIVE_API",
  "markdownVatCertificate": "# EU VIES VAT & REVERSE CHARGE COMPLIANCE CERTIFICATE: IE6388047V\n\n## 1. Tax Identification & Jurisdiction\n- **Full EU VAT Number:** `IE6388047V`\n- **Member State Code:** `IE` (National ID: `6388047V`)\n- **Seller / Invoicing Jurisdiction:** `DE`\n- **Structural Regex Checksum:** PASS (Valid Format)\n- **VIES Cross-Border Status:** ACTIVE (Valid for Intra-EU)\n\n## 2. Registered Corporate Entity Details\n- **Legal Trader Name:** GOOGLE IRELAND LIMITED\n- **Registered Address:** 3RD FLOOR, GORDON HOUSE, BARROW STREET, DUBLIN 4\n- **Verification Source:** `EU_VIES_LIVE_API`\n\n## 3. Tax Determination (Directive 2006/112/EC Art. 196)\n- **Invoicing Treatment:** **ELIGIBLE_INTRA_EU_0_VAT_REVERSE_CHARGE**\n- **Audit Risk Score:** **5/100** (Lower is safer)"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~eu-vies-vat-tax-compliance-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "vatNumbers": "IE6388047V, DE811128135, FR40303265045",
  "requesterCountryCode": "DE",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~eu-vies-vat-tax-compliance-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"vatNumbers": "IE6388047V, DE811128135, FR40303265045", "requesterCountryCode": "DE", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
