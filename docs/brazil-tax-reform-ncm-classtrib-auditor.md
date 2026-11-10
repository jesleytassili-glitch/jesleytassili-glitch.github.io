# Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-tax-reform-ncm-classtrib-auditor.html](https://jesleytassili-glitch.github.io/docs/brazil-tax-reform-ncm-classtrib-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-tax-reform-ncm-classtrib-auditor.md](https://jesleytassili-glitch.github.io/docs/brazil-tax-reform-ncm-classtrib-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-tax-reform-ncm-classtrib-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-tax-reform-ncm-classtrib-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-tax-reform-ncm-classtrib-auditor](https://apify.com/b2b-quant-apis/brazil-tax-reform-ncm-classtrib-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+vies+vat+tax+compliance+auditor+api/14654](https://zylalabs.com/api-marketplace/legal+%26+compliance/eu+vies+vat+tax+compliance+auditor+api/14654)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-tax-reform-ncm-classtrib-auditor](https://rapidapi.com/b2bquantapis/api/brazil-tax-reform-ncm-classtrib-auditor)

## Executive Overview
Maps Brazilian NCM product catalogs and audits NF-e XML invoices for the 2026 Tax Reform (LC 214/2025 - IBS, CBS, and Imposto Seletivo). Returns cClassTrib, CST, reduction percentages, legal annexes, and compliance alerts.

### Enterprise B2B Value Proposition (Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor)
- **Target B2B Buyers:** Tax Automation ERPs, Accounting SaaS, eCommerce Checkout Engines, and Big4 Tax Auditors.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`NCM / NF-e Item Audited (LC 214/2025)`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-tax-reform-ncm-classtrib-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Taxes & Compliance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** brazil-tax-reform, ncm-auditor, ibs-cbs, classtrib, nfe-compliance, lc-214-2025, erp-tax-engine.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `catalogItems` | `array[object]` | Optional | List of products with 'ncm' (8 digits) and optional 'description' or 'sku' to map to 2026 IBS/CBS cClassTrib and CST. |
| `nfeXmlList` | `array[string]` | Optional | Optional list of raw NF-e / NFC-e XML strings to extract <det> items, validate 2026 <IBSCBS> tags, and map NCM -> cClassTrib. |
| `uf` | `string` | Optional | Two-letter Brazilian state for transition simulations (2026 test rate: 0.9% CBS + 0.1% IBS). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `sku` | `string` | SKU / Item extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `ncmFormatted` | `string` | NCM extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `description` | `string` | Description extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `cstIbsCbs` | `string` | CST (IBS/CBS) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `cClassTrib` | `string` | cClassTrib (6 digits) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `regimeName` | `string` | Tax Regime (2026) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `aliquotaReductionPct` | `number` | Reduction (%) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `impostoSeletivo` | `boolean` | Imposto Seletivo (IS) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `legalBasisLC214` | `string` | Legal Basis (LC 214/2025) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `confidenceScore` | `integer` | Confidence (%) extracted and validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `ncm` | `string` | ncm returned by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |
| `cbsTestRate2026Pct` | `number` | cbsTestRate2026Pct validated by Brazil Tax Reform 2026: NCM to cClassTrib & NF-e Auditor. |

## Verified Authentic Response Example
```json
{
  "sku": "ITEM-001",
  "ncm": "10063021",
  "ncmFormatted": "1006.30.21",
  "description": "Arroz beneficiado parboilizado tipo 1",
  "cstIbsCbs": "200",
  "cClassTrib": "200003",
  "regimeName": "Cesta Básica Nacional de Alimentos (Alíquota Zero — Redução de 100%)",
  "aliquotaReductionPct": 100.0,
  "cbsTestRate2026Pct": 0.0,
  "ibsTestRate2026Pct": 0.0,
  "impostoSeletivo": false,
  "legalBasisLC214": "Art. 125 e Anexo I da LC nº 214/2025",
  "confidenceScore": 96,
  "auditNotes": "Alíquota reduzida em 100% (Zero IBS/CBS). Conferir especificação exata do item no Anexo I.",
  "sourceType": "CATALOG_JSON"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-tax-reform-ncm-classtrib-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "catalogItems": [
    {
      "sku": "ITEM-001",
      "ncm": "10063021",
      "description": "Arroz beneficiado parboilizado tipo 1"
    },
    {
      "sku": "ITEM-002",
      "ncm": "30049099",
      "description": "Medicamento para uso humano em doses"
    },
    {
      "sku": "ITEM-003",
      "ncm": "22030000",
      "description": "Cerveja de malte em lata 350ml"
    },
    {
      "sku": "ITEM-004",
      "ncm": "84713012",
      "description": "Notebook portátil para processamento de dados"
    }
  ],
  "nfeXmlList": [],
  "uf": "SP"
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-tax-reform-ncm-classtrib-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"catalogItems": [{"sku": "ITEM-001", "ncm": "10063021", "description": "Arroz beneficiado parboilizado tipo 1"}, {"sku": "ITEM-002", "ncm": "30049099", "description": "Medicamento para uso humano em doses"}, {"sku": "ITEM-003", "ncm": "22030000", "description": "Cerveja de malte em lata 350ml"}, {"sku": "ITEM-004", "ncm": "84713012", "description": "Notebook portátil para processamento de dados"}], "nfeXmlList": [], "uf": "SP"}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
