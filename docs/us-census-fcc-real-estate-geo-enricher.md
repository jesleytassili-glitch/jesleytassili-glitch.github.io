# US Real Estate Census Tract, FIPS & PropTech Geo Enricher

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-census-fcc-real-estate-geo-enricher.html](https://jesleytassili-glitch.github.io/docs/us-census-fcc-real-estate-geo-enricher.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-census-fcc-real-estate-geo-enricher.md](https://jesleytassili-glitch.github.io/docs/us-census-fcc-real-estate-geo-enricher.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-census-fcc-real-estate-geo-enricher.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-census-fcc-real-estate-geo-enricher.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-census-fcc-real-estate-geo-enricher](https://apify.com/b2b-quant-apis/us-census-fcc-real-estate-geo-enricher)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645](https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Enriches U.S. commercial and residential real estate coordinates via official FCC & U.S. Census Bureau APIs (Zero-Key). Extracts 15-digit Block FIPS, 11-digit Census Tract, County FIPS, bounding boxes, and Property Underwriting Scores.

### Enterprise B2B Value Proposition (US Real Estate Census Tract, FIPS & PropTech Geo Enricher)
- **Target B2B Buyers:** PropTech Platforms, Mortgage Lenders (HMDA/CRA Compliance), Real Estate REITs, and Site Selection Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`U.S. Real Estate Census Tract & FIPS Enriched`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-census-fcc-real-estate-geo-enricher/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Data` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** us-census-fips, fcc-area-api, real-estate-analytics, geospatial-enrichment, census-tract, proptech, mortgage-hmda.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `coordinatesList` | `string` | Required | Semicolon-separated latitude,longitude pairs (e.g., '40.7128,-74.0060; 25.7617,-80.1918; 30.2672,-97.7431'). |
| `censusYear` | `string` | Optional | Decennial Census geography vintage ('2020' or '2010'). |
| `maxResults` | `integer` | Optional | Maximum number of U.S. property coordinate pairs to enrich (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `censusBlockFips` | `string` | Official 15-digit U.S. Census Block FIPS identifier. |
| `censusTractFips` | `string` | 11-digit Census Tract code used for HUD, Fannie Mae, and Opportunity Zone underwriting. |
| `countyFips` | `string` | Official 5-digit U.S. County FIPS code. |
| `countyName` | `string` | Official County or Parish name. |
| `stateCode` | `string` | Two-letter U.S. State or Territory code. |
| `stateName` | `string` | Full U.S. State name. |
| `latitude` | `number` | Property latitude coordinate. |
| `longitude` | `number` | Property longitude coordinate. |
| `realEstateInvestmentScore` | `integer` | Quantitative commercial corridor and metro tier score (0-100). |
| `bboxSummary` | `string` | Geographic bounding box coordinates [minLon, minLat, maxLon, maxLat]. |
| `markdownPropertyBrief` | `string` | Executive Markdown brief for real estate underwriting, insurance, and franchise siting. |

## Verified Authentic Response Example
```json
{
  "censusBlockFips": "360610031002008",
  "censusTractFips": "36061003100",
  "countyFips": "36061",
  "countyName": "New York County",
  "stateCode": "NY",
  "stateName": "New York",
  "latitude": 40.7128,
  "longitude": -74.006,
  "realEstateInvestmentScore": 100,
  "bboxSummary": "[-74.007225, 40.71217, -74.004059, 40.714166]",
  "markdownPropertyBrief": "# US REAL ESTATE CENSUS TRACT & FIPS UNDERWRITING BRIEF: New York County, NY\n\n## 1. Official U.S. Census Geography Identifiers\n- **15-Digit Census Block FIPS:** `360610031002008`\n- **11-Digit Census Tract FIPS (HUD / Opportunity Zone):** `36061003100`\n- **5-Digit County FIPS:** `36061`\n- **County & State:** New York County, New York (`NY`)\n\n## 2. Geospatial & PropTech Underwriting Intelligence\n- **Coordinates (Lat, Lon):** `40.7128, -74.006`\n- **Block Bounding Box:** `[-74.007225, 40.71217, -74.004059, 40.714166]`\n- **PropTech Institutional Liquidity Score:** **100/100**"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-census-fcc-real-estate-geo-enricher/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "coordinatesList": "40.7128,-74.0060; 25.7617,-80.1918; 30.2672,-97.7431",
  "censusYear": "2020",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-census-fcc-real-estate-geo-enricher/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"coordinatesList": "40.7128,-74.0060; 25.7617,-80.1918; 30.2672,-97.7431", "censusYear": "2020", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
