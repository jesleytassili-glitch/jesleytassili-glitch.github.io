# Brazil IBGE CNAE 2.3 & Municipal Code B2B Tax Enricher

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-ibge-cnae-municipal-b2b-expansion-enricher.html](https://jesleytassili-glitch.github.io/docs/brazil-ibge-cnae-municipal-b2b-expansion-enricher.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-ibge-cnae-municipal-b2b-expansion-enricher.md](https://jesleytassili-glitch.github.io/docs/brazil-ibge-cnae-municipal-b2b-expansion-enricher.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-ibge-cnae-municipal-b2b-expansion-enricher.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-ibge-cnae-municipal-b2b-expansion-enricher.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-ibge-cnae-municipal-b2b-expansion-enricher](https://apify.com/b2b-quant-apis/brazil-ibge-cnae-municipal-b2b-expansion-enricher)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/location+%26+mapping/brazil+cep+geocoordinates+ibge+code+api/14663](https://zylalabs.com/api-marketplace/location+%26+mapping/brazil+cep+geocoordinates+ibge+code+api/14663)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-ibge-cnae-municipal-b2b-expansion-enricher](https://rapidapi.com/b2bquantapis/api/brazil-ibge-cnae-municipal-b2b-expansion-enricher)

## Executive Overview
Enriches Brazilian CNAE 2.3 industry codes via official IBGE CONCLA APIs. Extracts permitted activities, tax exclusions, hierarchy (Section/Division/Class), and official 7-digit IBGE municipal codes for NF-e/NFS-e compliance.

### Enterprise B2B Value Proposition (Brazil IBGE CNAE 2.3 & Municipal Code B2B Tax Enricher)
- **Target B2B Buyers:** Accounting Automation Platforms, B2B Lead Scoring Engines, and Franchise Expansion Analysts.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Brazil IBGE CNAE 2.3 Subclass & Tax Activity Enriched`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-ibge-cnae-municipal-b2b-expansion-enricher/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** ibge-cnae, concla-subclass, brazil-tax-activities, municipal-expansion, b2b-market-sizing, company-classification, simples-nacional.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `cnaeCodes` | `string` | Required | Comma-separated 7-digit Brazilian CNAE codes (e.g., '6201501, 4711302, 8630503'). |
| `targetUf` | `string` | Optional | Two-letter Brazilian state UF code (e.g., SP, RJ, MG, PR). |
| `maxResults` | `integer` | Optional | Maximum number of CNAE subclass records to return (1 to 50). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `cnaeSubclassId` | `string` | Official 7-digit CNAE 2.3 subclass identifier. |
| `cnaeDescription` | `string` | Official IBGE CONCLA subclass description. |
| `sectionCode` | `string` | IBGE macro economic section. |
| `divisionDescription` | `string` | IBGE 2-digit division description. |
| `permittedActivitiesCount` | `integer` | Total specific activities covered by this CNAE. |
| `sampleActivities` | `string` | Top activities included in this CNAE. |
| `targetUf` | `string` | Queried Brazilian state UF. |
| `b2bFitScore` | `integer` | Quantitative score for B2B segmentation and fiscal clarity (0-100). |
| `markdownCnaeDossier` | `string` | Executive report for accountants, ERPs, and B2B lead segmentation. |

## Verified Authentic Response Example
```json
{
  "cnaeSubclassId": "6201501",
  "cnaeDescription": "DESENVOLVIMENTO DE PROGRAMAS DE COMPUTADOR SOB ENCOMENDA",
  "sectionCode": "J - INFORMAÇÃO E COMUNICAÇÃO",
  "divisionDescription": "ATIVIDADES DOS SERVIÇOS DE TECNOLOGIA DA INFORMAÇÃO",
  "permittedActivitiesCount": 5,
  "sampleActivities": "DESENVOLVIMENTO DE SISTEMAS E SOFTWARE SOB ENCOMENDA; PROGRAMAÇÃO DE SISTEMAS INFORMÁTICOS SOB ENCOMENDA; MODELAGEM DE BANCO DE DADOS SOB ENCOMENDA; DESENVOLVIMENTO DE APLICATIVO INFORMÁTICO SOB ENCOMENDA",
  "targetUf": "SP",
  "b2bFitScore": 98,
  "markdownCnaeDossier": "# BRAZIL IBGE CNAE 2.3 FISCAL & B2B SEGMENTATION DOSSIER: 6201501\n\n## 1. Official CONCLA / IBGE Classification\n- **CNAE Subclass (7 Digits):** `6201501`\n- **Official Description:** **DESENVOLVIMENTO DE PROGRAMAS DE COMPUTADOR SOB ENCOMENDA**\n- **Macro Section:** `J - INFORMAÇÃO E COMUNICAÇÃO`\n- **Economic Division:** `ATIVIDADES DOS SERVIÇOS DE TECNOLOGIA DA INFORMAÇÃO`\n- **Target State UF:** `SP`\n\n## 2. Covered Tax Activities & B2B ICP Score\n- **B2B Tax & Expansion Fit Score:** **98/100**\n- **Permitted Activities Count:** `5`\n- **Sample Covered Activities:** DESENVOLVIMENTO DE SISTEMAS E SOFTWARE SOB ENCOMENDA; PROGRAMAÇÃO DE SISTEMAS INFORMÁTICOS SOB ENCOMENDA; MODELAGEM DE BANCO DE DADOS SOB ENCOMENDA; DESENVOLVIMENTO DE APLICATIVO INFORMÁTICO SOB ENCOMENDA"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-ibge-cnae-municipal-b2b-expansion-enricher/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "cnaeCodes": "6201501,4711302,8630503",
  "targetUf": "SP",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-ibge-cnae-municipal-b2b-expansion-enricher/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"cnaeCodes": "6201501,4711302,8630503", "targetUf": "SP", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
