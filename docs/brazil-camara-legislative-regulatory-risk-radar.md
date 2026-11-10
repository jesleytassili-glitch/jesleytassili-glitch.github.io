# Brazil Congress Legislative Bills & Tax Regulatory Risk Radar

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-camara-legislative-regulatory-risk-radar.html](https://jesleytassili-glitch.github.io/docs/brazil-camara-legislative-regulatory-risk-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-camara-legislative-regulatory-risk-radar.md](https://jesleytassili-glitch.github.io/docs/brazil-camara-legislative-regulatory-risk-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-camara-legislative-regulatory-risk-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-camara-legislative-regulatory-risk-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-camara-legislative-regulatory-risk-radar](https://apify.com/b2b-quant-apis/brazil-camara-legislative-regulatory-risk-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/brazil+camara+legislative+regulatory+risk+api/14652](https://zylalabs.com/api-marketplace/legal+%26+compliance/brazil+camara+legislative+regulatory+risk+api/14652)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-camara-legislative-regulatory-risk-radar](https://rapidapi.com/b2bquantapis/api/brazil-camara-legislative-regulatory-risk-radar)

## Executive Overview
Monitors Brazilian Chamber of Deputies (Camara dos Deputados API v2) legislative bills (PL, PLP, PEC, MPV). Filters by sector/tax keyword, extracts official summary (ementa), presentation date, and Regulatory Risk Scores (0-100).

### Enterprise B2B Value Proposition (Brazil Congress Legislative Bills & Tax Regulatory Risk Radar)
- **Target B2B Buyers:** Government Relations (RIG) Teams, Corporate Legal Departments, Institutional Funds, and Law Firms.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Brazil Congress Legislative Bill & Tax Risk Analyzed`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-camara-legislative-regulatory-risk-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Data` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** brazil-congress-api, camara-deputados, legislative-radar, regulatory-risk, public-policy-tracker, gov-relations, pec-pl-plp.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `billType` | `string` | Required | Type of legislative bill: PL (Ordinary Law), PLP (Complementary Law), PEC (Constitutional Amendment), MPV (Provisional Measure). |
| `keyword` | `string` | Optional | Optional keyword to filter bill summaries (e.g., tributo, imposto, credito, trabalho, digital). Leave empty for latest bills. |
| `maxResults` | `integer` | Optional | Maximum number of legislative propositions to return (1 to 50). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `propositionId` | `string` | Official Camara dos Deputados proposition ID. |
| `billCode` | `string` | Formatted legislative identifier (e.g., PL 1156/2026). |
| `billType` | `string` | PL, PLP, PEC, or MPV. |
| `billYear` | `integer` | Year the bill was introduced. |
| `presentationDate` | `string` | ISO timestamp of presentation. |
| `summaryEmenta` | `string` | Official summary of the legislative proposal. |
| `officialUri` | `string` | Direct link to the proposition record. |
| `regulatoryRiskScore` | `integer` | Quantitative corporate and tax impact score (0-100). |
| `markdownGovRelBrief` | `string` | Executive report for law firms, tax advisors, and corporate GovRel teams. |

## Verified Authentic Response Example
```json
{
  "propositionId": "2648838",
  "billCode": "PL 5662/2026",
  "billType": "PL",
  "billYear": 2026,
  "presentationDate": "2026-10-26T13:27",
  "summaryEmenta": "Altera a Lei nº 13.146, de 6 de julho de 2015 (Lei Brasileira de Inclusão da Pessoa com Deficiência), para assegurar a gratuidade do estacionamento vinculado a estabelecimento de saúde ou de habilitação e reabilitação para veículo utilizado no transporte de pessoa com deficiência com comprometimento de mobilidade.",
  "officialUri": "https://dadosabertos.camara.leg.br/api/v2/proposicoes/2648838",
  "regulatoryRiskScore": 76,
  "markdownGovRelBrief": "# BRAZIL CONGRESS LEGISLATIVE & REGULATORY RISK BRIEF: PL 5662/2026\n\n## 1. Proposition Identity\n- **Bill Code:** **`PL 5662/2026`**\n- **Proposition ID:** `2648838`\n- **Type / Year:** `PL / 2026`\n- **Presentation Date:** `2026-10-26T13:27`\n- **Official API URI:** https://dadosabertos.camara.leg.br/api/v2/proposicoes/2648838\n\n## 2. Corporate & Tax Impact Analysis\n- **Regulatory Impact & Risk Score:** **76/100**\n- **Official Summary (Ementa):** Altera a Lei nº 13.146, de 6 de julho de 2015 (Lei Brasileira de Inclusão da Pessoa com Deficiência), para assegurar a gratuidade do estacionamento vinculado a estabelecimento de saúde ou de habilitação e reabilitação para veículo utilizado no transporte de pessoa com deficiência com comprometimento de mobilidade."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-camara-legislative-regulatory-risk-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "billType": "PL",
  "keyword": "",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-camara-legislative-regulatory-risk-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"billType": "PL", "keyword": "", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
