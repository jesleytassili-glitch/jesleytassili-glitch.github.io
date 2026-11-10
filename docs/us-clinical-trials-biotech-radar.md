# US ClinicalTrials.gov Biotech & Pharma Study Radar

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-clinical-trials-biotech-radar.html](https://jesleytassili-glitch.github.io/docs/us-clinical-trials-biotech-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-clinical-trials-biotech-radar.md](https://jesleytassili-glitch.github.io/docs/us-clinical-trials-biotech-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-clinical-trials-biotech-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-clinical-trials-biotech-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-clinical-trials-biotech-radar](https://apify.com/b2b-quant-apis/us-clinical-trials-biotech-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+clinical+trials+biotech+radar+api/14662](https://zylalabs.com/api-marketplace/health+%26+fitness/us+clinical+trials+biotech+radar+api/14662)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
B2B clinical trials intelligence and biotech sponsor lead generator powered by the official U.S. NIH ClinicalTrials.gov API v2. Extracts recruiting studies, pharma sponsors, phases, drug interventions, enrollment counts, and site contacts with LLM-ready Markdown briefs.

### Enterprise B2B Value Proposition (US ClinicalTrials.gov Biotech & Pharma Study Radar)
- **Target B2B Buyers:** Contract Research Organizations (CROs), Biotech Venture Capitalists, and Pharma BD&L Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Clinical Trial & Biotech Sponsor Extracted`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-clinical-trials-biotech-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Medical` | Zyla API Hub `Healthcare`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** clinical-trials, biotech-intelligence, nih-clinicaltrials, pharma-pipeline, cro-leads, phase2-phase3, life-sciences.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `condition` | `string` | Optional | Disease, medical condition, or therapeutic area query (e.g., Diabetes, Non-Small Cell Lung Cancer, Obesity, Alzheimer). |
| `overallStatus` | `string` | Optional | Filter clinical studies by current recruitment status on ClinicalTrials.gov. |
| `maxResults` | `integer` | Optional | Maximum number of clinical trial records to fetch (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `nctId` | `string` | NCT ID extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `briefTitle` | `string` | Brief Title extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `overallStatus` | `string` | Status extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `leadSponsorName` | `string` | Lead Sponsor extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `leadSponsorClass` | `string` | Sponsor Class extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `phases` | `array[string]` | Phases extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `enrollmentCount` | `integer` | Enrollment extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `conditions` | `array[string]` | Conditions extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `locationsCount` | `integer` | Clinical Sites extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `studyUrl` | `string` | ClinicalTrials.gov URL extracted and validated by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `officialTitle` | `string` | officialTitle returned by US ClinicalTrials.gov Biotech & Pharma Study Radar. |
| `collaborators` | `array[string]` | collaborators array returned by US ClinicalTrials.gov Biotech & Pharma Study Radar. |

## Verified Authentic Response Example
```json
{
  "nctId": "NCT05835037",
  "briefTitle": "Effect of Zinc on Glucose Homeostasis",
  "officialTitle": "Clinical and Nutrigenetic Assessment of Zinc in Participants With Prediabetes",
  "overallStatus": "RECRUITING",
  "leadSponsorName": "University of Maryland, Baltimore",
  "leadSponsorClass": "OTHER",
  "collaborators": [],
  "studyType": "INTERVENTIONAL",
  "phases": [
    "PHASE4"
  ],
  "enrollmentCount": 200,
  "enrollmentType": "ESTIMATED",
  "conditions": [
    "Prediabetic State",
    "Hyperglycemia"
  ],
  "keywords": [],
  "interventions": [
    {
      "type": "DRUG",
      "name": "Zinc Gluconate 30 MG",
      "description": "Participants will take one tablet per day (30 mg Zinc gluconate) for 1 year"
    },
    {
      "type": "DRUG",
      "name": "Placebo",
      "description": "Participants will take one placebo tablet per day for 1 year"
    }
  ],
  "interventionNames": [
    "Zinc Gluconate 30 MG",
    "Placebo"
  ],
  "centralContacts": [
    {
      "name": "Toni I Pollin, PhD",
      "role": "CONTACT",
      "phone": "410-706-1630",
      "email": "tpollin@som.umaryland.edu"
    },
    {
      "name": "Hilary B Whitlatch, MD",
      "role": "CONTACT",
      "phone": "443-682-6800",
      "email": "hwhitlatch@som.umaryland.edu"
    }
  ],
  "locationsCount": 1,
  "sampleLocations": [
    {
      "facility": "Amish Research Clinic",
      "city": "Lancaster",
      "state": "Pennsylvania",
      "country": "United States",
      "status": "RECRUITING"
    }
  ],
  "startDate": "2024-02-16",
  "completionDate": "2028-07",
  "studyUrl": "https://clinicaltrials.gov/study/NCT05835037",
  "scrapedAt": "2026-11-03T21:16:50.826632+00:00",
  "markdownTrialBrief": "## [NCT05835037] Effect of Zinc on Glucose Homeostasis\n- **Official Title**: Clinical and Nutrigenetic Assessment of Zinc in Participants With Prediabetes\n- **Recruitment Status**: `RECRUITING`\n- **Lead Sponsor**: University of Maryland, Baltimore (`OTHER`)\n- **Trial Phase(s)**: `PHASE4`\n- **Target Enrollment**: 200 participants\n- **Conditions**: Prediabetic State, Hyperglycemia\n- **Participating Clinical Sites**: 1 locations\n- **Study URL**: https://clinicaltrials.gov/study/NCT05835037\n- **Interventions / Drugs**:\n  - **DRUG**: Zinc Gluconate 30 MG — Participants will take one tablet per day (30 mg Zinc gluconate) for 1 year\n  - **DRUG**: Placebo — Participants will take one placebo tablet per day for 1 year\n- **Central Study Contacts**:\n  - **Toni I Pollin, PhD** (CONTACT) | Email: `tpollin@som.umaryland.edu` | Phone: `410-706-1630`\n  - **Hilary B Whitlatch, MD** (CONTACT) | Email: ..."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-clinical-trials-biotech-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "condition": "Diabetes",
  "overallStatus": "RECRUITING",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-clinical-trials-biotech-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"condition": "Diabetes", "overallStatus": "RECRUITING", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
