# Brazil CEP Geocoordinates, IBGE Code & Logistics Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-cep-geocoordinates-logistics-auditor.html](https://jesleytassili-glitch.github.io/docs/brazil-cep-geocoordinates-logistics-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-cep-geocoordinates-logistics-auditor.md](https://jesleytassili-glitch.github.io/docs/brazil-cep-geocoordinates-logistics-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-cep-geocoordinates-logistics-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-cep-geocoordinates-logistics-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-cep-geocoordinates-logistics-auditor](https://apify.com/b2b-quant-apis/brazil-cep-geocoordinates-logistics-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/location+%26+mapping/brazil+cep+geocoordinates+ibge+code+api/14663](https://zylalabs.com/api-marketplace/location+%26+mapping/brazil+cep+geocoordinates+ibge+code+api/14663)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-cep-geocoordinates-logistics-auditor](https://rapidapi.com/b2bquantapis/api/brazil-cep-geocoordinates-logistics-auditor)

## Executive Overview
Batch geocodes and validates Brazilian 8-digit postal codes (CEPs) via official Brazilian postal & IBGE registries. Extracts Latitude/Longitude, 7-digit IBGE city code (for NF-e/CT-e), state UF, neighborhood, and Last-Mile Delivery Scores (0-100).

### Enterprise B2B Value Proposition (Brazil CEP Geocoordinates, IBGE Code & Logistics Auditor)
- **Target B2B Buyers:** eCommerce Checkout Flows, Last-Mile Delivery Routers, NF-e Issuers, and Retail Omni-Channel ERPs.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Brazil CEP Geocoordinates & IBGE City Code Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-cep-geocoordinates-logistics-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Logistics` | Zyla API Hub `Logistics & Shipping`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** brazil-cep-lookup, postal-geocoding, ibge-municipality-code, nfe-address-validator, last-mile-logistics, ddd-lookup, ecommerce-checkout.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `ceps` | `string` | Required | Comma-separated Brazilian postal codes (e.g., '01310100, 20040002, 30140071'). |
| `maxResults` | `integer` | Optional | Maximum number of CEP records to return (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `cep` | `string` | Standardized 8-digit Brazilian postal code. |
| `stateUf` | `string` | Two-letter Brazilian state code. |
| `cityName` | `string` | Official municipality name. |
| `neighborhood` | `string` | District or neighborhood. |
| `street` | `string` | Street address. |
| `ibgeCityCode` | `string` | Official 7-digit IBGE municipality code for NF-e/CT-e. |
| `latitude` | `number` | WGS84 Latitude coordinate. |
| `longitude` | `number` | WGS84 Longitude coordinate. |
| `logisticsReadinessScore` | `integer` | Quantitative score for last-mile routing and tax invoice completeness (0-100). |
| `markdownLogisticsDossier` | `string` | Executive report for e-commerce, TMS/WMS, and ERP tax engines. |

## Verified Authentic Response Example
```json
{
  "cep": "01310100",
  "stateUf": "SP",
  "cityName": "São Paulo",
  "neighborhood": "Bela Vista",
  "street": "Avenida Paulista",
  "ibgeCityCode": "3550308",
  "latitude": -23.5475,
  "longitude": -46.63611,
  "logisticsReadinessScore": 100,
  "markdownLogisticsDossier": "# BRAZIL CEP GEOCOORDINATES & NF-e LOGISTICS DOSSIER: 01310100\n\n## 1. Standardized Address & Tax Jurisdiction\n- **CEP (8 Digits):** `01310100`\n- **Municipality / State UF:** **São Paulo - SP**\n- **IBGE 7-Digit City Code (NF-e/CT-e):** `3550308`\n- **Neighborhood:** `Bela Vista`\n- **Street / Logradouro:** Avenida Paulista\n\n## 2. Last-Mile Geocoordinates & Readiness\n- **Logistics & NF-e Readiness Score:** **100/100**\n- **WGS84 Coordinates:** `(-23.5475, -46.63611)`"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-cep-geocoordinates-logistics-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "ceps": "01310100,20040002,30140071",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-cep-geocoordinates-logistics-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"ceps": "01310100,20040002,30140071", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
