# US Healthcare NPI Doctor & Clinic Lead Enricher (CMS API)

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-healthcare-npi-provider-lead-enricher.html](https://jesleytassili-glitch.github.io/docs/us-healthcare-npi-provider-lead-enricher.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-healthcare-npi-provider-lead-enricher.md](https://jesleytassili-glitch.github.io/docs/us-healthcare-npi-provider-lead-enricher.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-healthcare-npi-provider-lead-enricher.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-healthcare-npi-provider-lead-enricher.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-healthcare-npi-provider-lead-enricher](https://apify.com/b2b-quant-apis/us-healthcare-npi-provider-lead-enricher)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+healthcare+npi+provider+lead+enricher+api/14661](https://zylalabs.com/api-marketplace/health+%26+fitness/us+healthcare+npi+provider+lead+enricher+api/14661)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
B2B healthcare lead extractor and enricher for US doctors, dentists, clinics, and hospitals using the official CMS NPPES NPI Registry API v2.1. Extracts NPI-1 and NPI-2 records, practice addresses, phone numbers, primary taxonomy, state licenses, and AI-ready lead dossiers.

### Enterprise B2B Value Proposition (US Healthcare NPI Doctor & Clinic Lead Enricher (CMS API))
- **Target B2B Buyers:** MedTech Sales Teams, Healthcare CRMs, Credentialing Platforms, and Digital Health Directories.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`US NPI Healthcare Provider Lead Enriched`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-healthcare-npi-provider-lead-enricher/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Medical` | Zyla API Hub `Healthcare`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** npi-registry, nppes-cms, healthcare-leads, medical-providers, doctor-lookup, hipaa-kyb, pharma-crm.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `state` | `string` | Optional | Two-letter US State code (e.g., FL, NY, CA, TX). |
| `city` | `string` | Optional | Optional city filter (e.g., Miami, Orlando, Los Angeles). |
| `taxonomyDescription` | `string` | Optional | Specialty/Taxonomy e.g. Dentist, Dermatology, Internal Medicine, Physical Therapist. |
| `enumerationType` | `string` | Optional | Filter by Individual Providers (NPI-1), Organizations/Clinics (NPI-2), or All. |
| `postalCode` | `string` | Optional | Optional US ZIP code prefix (e.g., 331, 33131). |
| `maxResults` | `integer` | Optional | Maximum number of healthcare provider leads to extract and enrich (1 to 200). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `npiNumber` | `string` | NPI Number |
| `providerType` | `string` | Provider Type |
| `fullNameOrOrgName` | `string` | Full Name / Organization |
| `primarySpecialty` | `string` | Primary Specialty |
| `LicenseNumber` | `string` | State License Number |
| `city` | `string` | City |
| `state` | `string` | State |
| `phone` | `string` | Direct Phone |
| `addressLine` | `string` | Practice Address |
| `leadQualityScore` | `integer` | Lead Quality Score (0-100) |
| `markdownLeadCard` | `string` | Markdown Lead Dossier |
| `enumerationType` | `string` | enumerationType returned by US Healthcare NPI Doctor & Clinic Lead Enricher (CMS API). |

## Verified Authentic Response Example
```json
{
  "npiNumber": "1104969039",
  "providerType": "NPI-2 (Organization)",
  "enumerationType": "NPI-2",
  "fullNameOrOrgName": "183 DENTAL GROUP, PA",
  "credential": "N/A",
  "primarySpecialty": "Dentist, General Practice",
  "taxonomyCode": "1223G0001X",
  "LicenseNumber": "DN 12408",
  "licenseNumber": "DN 12408",
  "licenseState": "FL",
  "city": "MIAMI",
  "state": "FL",
  "postalCode": "33169-4470",
  "phone": "305-652-8338",
  "fax": "305-653-5807",
  "addressLine": "636 NW 183RD ST",
  "authorizedOfficial": "TODD SMITH (dentist)",
  "status": "Active",
  "lastUpdated": "2008-06-13",
  "leadQualityScore": 100,
  "markdownLeadCard": "### 183 DENTAL GROUP, PA (NPI: 1104969039)\n- **Type:** NPI-2 (Organization) | **Specialty:** Dentist, General Practice (`1223G0001X`)\n- **State License:** `DN 12408` (FL) | **Lead Score:** 100/100\n- **Practice Address:** 636 NW 183RD ST, MIAMI, FL 33169-4470\n- **Direct Phone:** 305-652-8338 | **Fax:** 305-653-5807",
  "extractedAt": "2026-11-03T21:16:47.797009+00:00"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-healthcare-npi-provider-lead-enricher/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "state": "FL",
  "city": "Miami",
  "taxonomyDescription": "Dentist",
  "enumerationType": "ALL",
  "postalCode": "",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-healthcare-npi-provider-lead-enricher/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"state": "FL", "city": "Miami", "taxonomyDescription": "Dentist", "enumerationType": "ALL", "postalCode": "", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
