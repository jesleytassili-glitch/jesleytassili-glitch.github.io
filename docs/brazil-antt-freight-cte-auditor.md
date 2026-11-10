# Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-antt-freight-cte-auditor.html](https://jesleytassili-glitch.github.io/docs/brazil-antt-freight-cte-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-antt-freight-cte-auditor.md](https://jesleytassili-glitch.github.io/docs/brazil-antt-freight-cte-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-antt-freight-cte-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-antt-freight-cte-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-antt-freight-cte-auditor](https://apify.com/b2b-quant-apis/brazil-antt-freight-cte-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645](https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-antt-freight-cte-auditor](https://rapidapi.com/b2bquantapis/api/brazil-antt-freight-cte-auditor)

## Executive Overview
Calculates the mandatory Brazilian ANTT minimum road freight floor (Lei 13.703/2018 - CCD x km + CC) and audits CT-e 4.00 XML invoices in batch to prevent automatic ANTT/SEFAZ fines.

### Enterprise B2B Value Proposition (Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor)
- **Target B2B Buyers:** Transportation Management Systems (TMS), 3PL Logistics Operators, and Supply Chain Controllers.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`ANTT Freight Route / CT-e Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-antt-freight-cte-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Logistics` | Zyla API Hub `Logistics & Shipping`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** freight-audit, antt-minimum-floor, cte-xml, logistics-compliance, road-transport, tms-integration, shipping-cost.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `routes` | `array[object]` | Optional | List of freight operations to audit against the ANTT Minimum Freight Table (Tabela A - Lotação). |
| `cteXmlList` | `array[string]` | Optional | Optional list of raw CT-e XML strings to extract <vTPrest>, origin/destination, and audit ANTT compliance. |
| `defaultAxles` | `integer` | Optional | Number of axles (2 to 9) to assume when auditing raw CT-e XML files. |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `routeId` | `string` | ID / CT-e extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `origin` | `string` | Origin extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `destination` | `string` | Destination extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `distanceKm` | `number` | Distance (km) extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `axles` | `integer` | Axles extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `cargoType` | `string` | Cargo Type extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `anttMinimumFloorBRL` | `number` | ANTT Floor (BRL) extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `chargedFreightBRL` | `number` | Charged Freight (BRL) extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `differenceBRL` | `number` | Difference (BRL) extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `complianceStatus` | `string` | ANTT Status extracted and validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `sourceType` | `string` | sourceType returned by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |
| `ccdRatePerKm` | `number` | ccdRatePerKm validated by Brazil ANTT Minimum Freight Calculator & CT-e XML Batch Auditor. |

## Verified Authentic Response Example
```json
{
  "routeId": "ROT-001",
  "sourceType": "ROUTE_SIMULATION",
  "origin": "Campinas/SP",
  "destination": "Goiânia/GO",
  "distanceKm": 815.0,
  "axles": 6,
  "cargoType": "carga_geral",
  "ccdRatePerKm": 6.678,
  "ccLoadUnloadFee": 681.9,
  "anttMinimumFloorBRL": 6124.47,
  "chargedFreightBRL": 6800.0,
  "differenceBRL": 675.53,
  "complianceStatus": "CONFORME_ACIMA_DO_PISO",
  "estimatedFineRiskBRL": 0.0,
  "recommendedAction": "Operação regular acima do piso mínimo obrigatório da ANTT."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-antt-freight-cte-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "routes": [
    {
      "routeId": "ROT-001",
      "origin": "Campinas/SP",
      "destination": "Goiânia/GO",
      "distanceKm": 815,
      "axles": 6,
      "cargoType": "carga_geral",
      "chargedFreightBRL": 6800.0
    }
  ],
  "cteXmlList": [],
  "defaultAxles": 6
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-antt-freight-cte-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"routes": [{"routeId": "ROT-001", "origin": "Campinas/SP", "destination": "Goiânia/GO", "distanceKm": 815, "axles": 6, "cargoType": "carga_geral", "chargedFreightBRL": 6800.0}], "cteXmlList": [], "defaultAxles": 6}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
