# US SEC EDGAR Filings & Insider Trading Radar (10-K/8-K/Form 4)

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-sec-edgar-filings-insider-radar.html](https://jesleytassili-glitch.github.io/docs/us-sec-edgar-filings-insider-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-sec-edgar-filings-insider-radar.md](https://jesleytassili-glitch.github.io/docs/us-sec-edgar-filings-insider-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-sec-edgar-filings-insider-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-sec-edgar-filings-insider-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-sec-edgar-filings-insider-radar](https://apify.com/b2b-quant-apis/us-sec-edgar-filings-insider-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sec+edgar+filings+insider+radar+api/14655](https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sec+edgar+filings+insider+radar+api/14655)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Extracts and audits official U.S. SEC EDGAR corporate filings (10-K, 10-Q, 8-K, Form 4 Insider Trading) via data.sec.gov. Calculates governance risk scores (0-100) and generates Markdown legal/financial briefs for M&A, hedge funds, and AI RAG agents.

### Enterprise B2B Value Proposition (US SEC EDGAR Filings & Insider Trading Radar (10-K/8-K/Form 4))
- **Target B2B Buyers:** Quantitative Hedge Funds, Equity Research Platforms, WealthTech Apps, and M&A Advisory Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`SEC EDGAR Filing & Governance Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-sec-edgar-filings-insider-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Finance` | Zyla API Hub `Finance`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** sec-edgar, 10k-10q-8k, form-4-insider, quantitative-finance, corporate-governance, cik-lookup, equity-research.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `tickerOrCik` | `string` | Required | Public company stock ticker (e.g., 'AAPL', 'MSFT', 'NVDA', 'TSLA', 'JPM') or 10-digit SEC Central Index Key (e.g., '0000320193'). |
| `formType` | `string` | Optional | Filter by specific SEC regulatory form type or select ALL. |
| `keyword` | `string` | Optional | Optional filter in primary document description or 8-K items (e.g., '5.02', '2.02', 'acquisition', 'restatement'). |
| `maxResults` | `integer` | Optional | Maximum number of SEC EDGAR filings to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `accessionNumber` | `string` | Unique SEC EDGAR filing accession identifier. |
| `cik` | `string` | Official 10-digit SEC Central Index Key. |
| `ticker` | `string` | Primary exchange stock ticker symbol. |
| `companyName` | `string` | Official registrant entity name on file with the SEC. |
| `formType` | `string` | SEC regulatory filing form code (10-K, 10-Q, 8-K, 4, etc.). |
| `filingDate` | `string` | Date the filing was accepted by SEC EDGAR (YYYY-MM-DD). |
| `reportDate` | `string` | Period of report covered by the filing (YYYY-MM-DD). |
| `governanceAlertScore` | `integer` | Quantitative materiality & governance attention score (0-100). |
| `itemsSummary` | `string` | Reported 8-K item codes or primary filing description. |
| `edgarDocumentUrl` | `string` | Direct URL to the official filing document on sec.gov/Archives. |
| `markdownGovernanceBrief` | `string` | Executive Markdown dossier ready for financial due diligence and LLM RAG ingestion. |

## Verified Authentic Response Example
```json
{
  "accessionNumber": "0000320193-26-000026",
  "cik": "0000320193",
  "ticker": "AAPL",
  "companyName": "Apple Inc.",
  "formType": "10-K",
  "filingDate": "2026-11-03",
  "reportDate": "2026-09-26",
  "governanceAlertScore": 84,
  "itemsSummary": "10-K",
  "edgarDocumentUrl": "https://www.sec.gov/Archives/edgar/data/320193/000032019326000026/aapl-20260926.htm",
  "markdownGovernanceBrief": "# SEC EDGAR GOVERNANCE & COMPLIANCE BRIEF: AAPL (10-K)\n\n## 1. Registrant & Filing Identification\n- **Company Name:** Apple Inc.\n- **Ticker / CIK:** `AAPL` / `0000320193`\n- **Accession Number:** `0000320193-26-000026`\n- **Form Type:** `10-K` (STANDARD STATUTORY DISCLOSURE)\n- **Governance Alert Score:** **84/100**\n\n## 2. Regulatory Timeline & Disclosure Scope\n- **SEC Filing Date:** 2026-11-03\n- **Period of Report:** 2026-09-26\n- **Material Items / Primary Description:** 10-K\n- **Official SEC EDGAR Archive URL:** https://www.sec.gov/Archives/edgar/data/320193/000032019326000026/aapl-20260926.htm"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-sec-edgar-filings-insider-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "tickerOrCik": "AAPL",
  "formType": "10-K",
  "keyword": "",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-sec-edgar-filings-insider-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"tickerOrCik": "AAPL", "formType": "10-K", "keyword": "", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
