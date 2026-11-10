# Brazil Pix ISPB, COMPE & CVM Financial Institution KYB Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-pix-ispb-cvm-financial-kyb-auditor.html](https://jesleytassili-glitch.github.io/docs/brazil-pix-ispb-cvm-financial-kyb-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-pix-ispb-cvm-financial-kyb-auditor.md](https://jesleytassili-glitch.github.io/docs/brazil-pix-ispb-cvm-financial-kyb-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-pix-ispb-cvm-financial-kyb-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-pix-ispb-cvm-financial-kyb-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-pix-ispb-cvm-financial-kyb-auditor](https://apify.com/b2b-quant-apis/brazil-pix-ispb-cvm-financial-kyb-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/finance+%26+payments/brazil+bcb+ptax+sgs+financial+contract+indexer+api/14658](https://zylalabs.com/api-marketplace/finance+%26+payments/brazil+bcb+ptax+sgs+financial+contract+indexer+api/14658)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-pix-ispb-cvm-financial-kyb-auditor](https://rapidapi.com/b2bquantapis/api/brazil-pix-ispb-cvm-financial-kyb-auditor)

## Executive Overview
Audits Brazilian banks, payment institutions, and FinTechs against official Central Bank SPI Pix (ISPB) and COMPE directories. Verifies direct vs. indirect settlement participation, operational status, and AML/KYB Risk Scores (0-100).

### Enterprise B2B Value Proposition (Brazil Pix ISPB, COMPE & CVM Financial Institution KYB Auditor)
- **Target B2B Buyers:** Payment Service Providers (PSPs), Banking-as-a-Service (BaaS) Platforms, and Treasury Reconciliation Systems.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Brazil Pix ISPB & SPI Financial Institution Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-pix-ispb-cvm-financial-kyb-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Finance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** brazil-pix-ispb, str-spi-participants, bank-routing-kyb, bacen-institutions, payment-clearing, fintech-compliance, compe-ispb.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `institutionQuery` | `string` | Required | Institution name keyword or 8-digit ISPB code (e.g., 'Itau', 'Nu Pagamentos', 'Banco do Brasil', '00000000'). |
| `onlyDirectPix` | `boolean` | Optional | When enabled, filters only institutions with direct settlement accounts in the Central Bank SPI. |
| `maxResults` | `integer` | Optional | Maximum number of audited financial institutions to return (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `ispbCode` | `string` | Official Central Bank of Brazil ISPB identifier. |
| `institutionName` | `string` | Full corporate name registered in the SPI. |
| `shortName` | `string` | Abbreviated clearing name. |
| `participationModality` | `string` | Role in the Pix ecosystem. |
| `participationType` | `string` | Direct (Direta) or Indirect (Indireta) settlement. |
| `operationStartDate` | `string` | Official Pix SPI activation timestamp. |
| `kybTrustScore` | `integer` | Quantitative AML/KYB clearing reliability score (0-100). |
| `markdownKybDossier` | `string` | Executive report for FinTech BaaS, treasury, and AML compliance teams. |

## Verified Authentic Response Example
```json
{
  "ispbCode": "00556603",
  "institutionName": "BANCO BARI S.A.",
  "shortName": "BANCO BARI S.A.",
  "participationModality": "Provedor de Conta Transacional",
  "participationType": "Direta",
  "operationStartDate": "N/A",
  "kybTrustScore": 95,
  "markdownKybDossier": "# BRAZIL CENTRAL BANK PIX (ISPB) KYB & CLEARING DOSSIER: BANCO BARI S.A.\n\n## 1. Institution Clearing Identity\n- **ISPB Code (8 Digits):** `00556603`\n- **Legal Institution Name:** **BANCO BARI S.A.**\n- **Short Clearing Name:** `BANCO BARI S.A.`\n\n## 2. SPI Settlement & AML/KYB Assessment\n- **KYB & Clearing Trust Score:** **95/100**\n- **SPI Settlement Type:** **`Direta`**\n- **Participation Modality:** `Provedor de Conta Transacional`\n- **Operation Start Date:** `N/A`"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-pix-ispb-cvm-financial-kyb-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "institutionQuery": "Banco",
  "onlyDirectPix": true,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-pix-ispb-cvm-financial-kyb-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"institutionQuery": "Banco", "onlyDirectPix": true, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
