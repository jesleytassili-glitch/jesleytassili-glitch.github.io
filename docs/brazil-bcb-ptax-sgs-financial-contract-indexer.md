# Brazil Central Bank PTAX, Selic, CDI & IPCA Contract Indexer

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-bcb-ptax-sgs-financial-contract-indexer.html](https://jesleytassili-glitch.github.io/docs/brazil-bcb-ptax-sgs-financial-contract-indexer.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-bcb-ptax-sgs-financial-contract-indexer.md](https://jesleytassili-glitch.github.io/docs/brazil-bcb-ptax-sgs-financial-contract-indexer.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-bcb-ptax-sgs-financial-contract-indexer.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-bcb-ptax-sgs-financial-contract-indexer.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-bcb-ptax-sgs-financial-contract-indexer](https://apify.com/b2b-quant-apis/brazil-bcb-ptax-sgs-financial-contract-indexer)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/finance+%26+payments/brazil+bcb+ptax+sgs+financial+contract+indexer+api/14658](https://zylalabs.com/api-marketplace/finance+%26+payments/brazil+bcb+ptax+sgs+financial+contract+indexer+api/14658)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-bcb-ptax-sgs-financial-contract-indexer](https://rapidapi.com/b2bquantapis/api/brazil-bcb-ptax-sgs-financial-contract-indexer)

## Executive Overview
Fetches official Central Bank of Brazil (BCB SGS & Olinda) macroeconomic series (Selic, CDI, IPCA, IGP-M, PTAX USD/EUR) and calculates automated B2B contract, lease, and treasury monetary adjustments.

### Enterprise B2B Value Proposition (Brazil Central Bank PTAX, Selic, CDI & IPCA Contract Indexer)
- **Target B2B Buyers:** Real Estate ERPs, LegalTech Contract Management Systems, FX Desks, and Brazilian FinTechs.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`BCB PTAX, Selic, CDI or IPCA Contract Index Calculated`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-bcb-ptax-sgs-financial-contract-indexer/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Finance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** banco-central-brasil, ptax-usd-brl, selic-cdi-ipca, igpm-indexer, contract-readjustment, brazil-macro-api, fintech-rates.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `indicators` | `string` | Required | Comma-separated BCB indicators: SELIC (432), IPCA (433), IGP-M (189), PTAX_USD (1), CDI (12). |
| `contractBaseValueBrl` | `number` | Optional | Principal value in BRL to simulate monetary adjustment against the latest indicator rate. |
| `maxResults` | `integer` | Optional | Maximum number of indicator records to return (1 to 20). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `indicatorCode` | `string` | BCB SGS series code. |
| `indicatorName` | `string` | Official macroeconomic indicator name. |
| `referenceDate` | `string` | Latest official publication date (DD/MM/YYYY). |
| `latestRateValue` | `number` | Latest official value or rate published by BCB. |
| `unitType` | `string` | Rate unit (% p.a., % p.m., BRL/USD). |
| `contractBaseValueBrl` | `number` | Input contract principal in BRL. |
| `adjustedContractValueBrl` | `number` | Simulated adjusted value in BRL. |
| `financialImpactScore` | `integer` | Quantitative treasury materiality score (0-100). |
| `markdownTreasuryBrief` | `string` | Executive report for CFOs, ERPs, and legal contract automation. |

## Verified Authentic Response Example
```json
{
  "indicatorCode": "432",
  "indicatorName": "Taxa Selic Meta (COPOM BCB)",
  "referenceDate": "04/11/2026",
  "latestRateValue": 13.75,
  "unitType": "% a.a.",
  "contractBaseValueBrl": 10000,
  "adjustedContractValueBrl": 11375,
  "financialImpactScore": 92,
  "markdownTreasuryBrief": "# BRAZIL CENTRAL BANK (BCB SGS) CONTRACT & TREASURY BRIEF: Taxa Selic Meta (COPOM BCB)\n\n## 1. Official Macroeconomic Series\n- **SGS Series Code:** `432`\n- **Indicator Name:** **Taxa Selic Meta (COPOM BCB)**\n- **Reference Date:** `04/11/2026`\n- **Latest Official Rate:** **`13.75 % a.a.`**\n\n## 2. Automated B2B Contract / Invoice Simulation\n- **Base Principal Value (BRL):** `R$ 10,000.00`\n- **Adjusted Value / FX Conversion:** **`R$ 11,375.00`**\n- **Financial Impact Score:** **92/100**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-bcb-ptax-sgs-financial-contract-indexer/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "indicators": "SELIC,IPCA,IGP-M,PTAX_USD",
  "contractBaseValueBrl": 10000,
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-bcb-ptax-sgs-financial-contract-indexer/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"indicators": "SELIC,IPCA,IGP-M,PTAX_USD", "contractBaseValueBrl": 10000, "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
