# Multi-ATS Tech Job Board & B2B Hiring Intent Signal Radar

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/multi-ats-tech-job-board-hiring-radar.html](https://jesleytassili-glitch.github.io/docs/multi-ats-tech-job-board-hiring-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/multi-ats-tech-job-board-hiring-radar.md](https://jesleytassili-glitch.github.io/docs/multi-ats-tech-job-board-hiring-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/multi-ats-tech-job-board-hiring-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/multi-ats-tech-job-board-hiring-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/multi-ats-tech-job-board-hiring-radar](https://apify.com/b2b-quant-apis/multi-ats-tech-job-board-hiring-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645](https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/multi-ats-tech-job-board-hiring-radar](https://rapidapi.com/b2bquantapis/api/multi-ats-tech-job-board-hiring-radar)

## Executive Overview
Extracts live tech job openings from public Greenhouse ATS boards (Zero-Proxy, Zero-Key). Detects B2B buying intent signals, remote status, department expansion, and scores hiring velocity (0-100) for sales and recruiting teams.

### Enterprise B2B Value Proposition (Multi-ATS Tech Job Board & B2B Hiring Intent Signal Radar)
- **Target B2B Buyers:** B2B Outbound Sales Teams, Executive Search Firms, Venture Capitalists, and RevOps Data Pipelines.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Tech Job Requisition & B2B Hiring Signal Extracted`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~multi-ats-tech-job-board-hiring-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** hiring-signals, greenhouse-ats, tech-jobs-api, b2b-buying-intent, recruiting-intelligence, sales-triggers, revops.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `companyBoards` | `string` | Required | Comma-separated Greenhouse board tokens (e.g., 'stripe,cloudflare,gitlab,airtable'). |
| `keyword` | `string` | Optional | Optional keyword to filter job titles or departments (e.g., 'engineer', 'security', 'sales', 'data'). |
| `maxResults` | `integer` | Optional | Maximum number of job openings to extract and score across boards (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `jobId` | `string` | Unique job requisition identifier on the ATS board. |
| `companyBoard` | `string` | Company slug on Greenhouse ATS. |
| `jobTitle` | `string` | Published title of the open position. |
| `department` | `string` | Primary organizational department. |
| `location` | `string` | Geographic location or remote region. |
| `workplaceType` | `string` | Remote, Hybrid, or Onsite classification. |
| `updatedAt` | `string` | ISO timestamp when the job requisition was updated. |
| `hiringIntentScore` | `integer` | Score measuring B2B budget expansion and technical buying intent (0-100). |
| `jobUrl` | `string` | Public URL to the job posting. |
| `techSignals` | `string` | Key technical and strategic hiring signals. |
| `markdownHiringBrief` | `string` | Executive Markdown dossier for B2B sales and technical recruiters. |

## Verified Authentic Response Example
```json
{
  "jobId": "8172487",
  "companyBoard": "stripe",
  "jobTitle": "Abuse Investigator",
  "department": "Engineering & Operations",
  "location": "Dublin",
  "workplaceType": "Onsite / Office",
  "updatedAt": "2026-10-29T10:42:09-04:00",
  "hiringIntentScore": 55,
  "jobUrl": "https://stripe.com/jobs/search?gh_jid=8172487",
  "techSignals": "Active Departmental Headcount Growth",
  "markdownHiringBrief": "# B2B HIRING INTENT & ATS SIGNAL BRIEF: STRIPE — Abuse Investigator\n\n## 1. Position & Organization Summary\n- **Company ATS Board:** `stripe`\n- **Requisition ID:** `8172487`\n- **Job Title:** **Abuse Investigator**\n- **Department:** Engineering & Operations\n- **Location / Workplace:** Dublin (Onsite / Office)\n\n## 2. B2B Buying Intent & Budget Intelligence\n- **B2B Hiring Intent Score:** **55/100**\n- **Detected Budget Signals:** Active Departmental Headcount Growth\n- **Last Updated:** 2026-10-29T10:42:09-04:00\n- **Direct Application / Requisition URL:** https://stripe.com/jobs/search?gh_jid=8172487"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~multi-ats-tech-job-board-hiring-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "companyBoards": "stripe,cloudflare",
  "keyword": "engineer",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~multi-ats-tech-job-board-hiring-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"companyBoards": "stripe,cloudflare", "keyword": "engineer", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
