# US FDA Recalls & Safety Monitor (Food, Drug & Devices)

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-fda-recalls-safety-monitor.html](https://jesleytassili-glitch.github.io/docs/us-fda-recalls-safety-monitor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-fda-recalls-safety-monitor.md](https://jesleytassili-glitch.github.io/docs/us-fda-recalls-safety-monitor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-fda-recalls-safety-monitor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-fda-recalls-safety-monitor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-fda-recalls-safety-monitor](https://apify.com/b2b-quant-apis/us-fda-recalls-safety-monitor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646](https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Monitors and enriches official U.S. FDA enforcement recall reports across Food, Drugs, and Medical Devices via openFDA. Calculates hazard severity scores (0-100) and generates Markdown legal briefs for Product Liability law firms and retail compliance.

### Enterprise B2B Value Proposition (US FDA Recalls & Safety Monitor (Food, Drug & Devices))
- **Target B2B Buyers:** Pharmaceutical Compliance Teams, Hospital Pharmacies, Retail Supply Chains, and InsurTech Underwriters.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`US FDA Enforcement Recall Extracted`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-fda-recalls-safety-monitor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Medical` | Zyla API Hub `Healthcare`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** fda-recalls, openfda, drug-safety, medical-device-recalls, food-safety, supply-chain-risk, pharmacovigilance.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `domain` | `string` | Required | Select the FDA enforcement category to monitor: food, drug, or device. |
| `classification` | `string` | Optional | Filter recalls by FDA hazard severity class (Class I = highest life-threatening risk, Class II = moderate/reversible risk, Class III = low risk). |
| `keyword` | `string` | Optional | Optional search keyword in reason_for_recall or product_description (e.g., 'salmonella', 'listeria', 'undeclared', 'pacemaker'). |
| `state` | `string` | Optional | Optional 2-letter US State of recalling firm (e.g., 'CA', 'NY', 'TX', 'FL'). |
| `maxResults` | `integer` | Optional | Maximum number of recall enforcement records to fetch (1 to 200). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `recallNumber` | `string` | Official FDA recall event or enforcement number. |
| `domain` | `string` | Regulatory domain (food, drug, device). |
| `classification` | `string` | FDA hazard severity class (Class I, Class II, Class III). |
| `severityScore` | `integer` | Quantitative risk score based on hazard class, recall status, and nationwide distribution. |
| `recallingFirm` | `string` | Manufacturer, distributor, or firm initiating the recall. |
| `state` | `string` | 2-letter US State code of the recalling firm. |
| `status` | `string` | Current enforcement status (Ongoing, Completed, Terminated, Pending). |
| `reportDate` | `string` | Formatted FDA enforcement report date (YYYY-MM-DD). |
| `reasonForRecall` | `string` | Official FDA summary of the defect, contamination, or safety hazard. |
| `productDescription` | `string` | Detailed description of the recalled product, packaging, and brand. |
| `markdownLegalBrief` | `string` | Ready-to-use Markdown dossier for Product Liability litigation and supply chain QA. |
| `eventId` | `string` | eventId returned by US FDA Recalls & Safety Monitor (Food, Drug & Devices). |

## Verified Authentic Response Example
```json
{
  "recallNumber": "D-0026-2027",
  "eventId": "99867",
  "domain": "drug",
  "classification": "Class II",
  "severityScore": 75,
  "recallingFirm": "Carolina Infusion, LLC",
  "city": "Ridgeland",
  "state": "SC",
  "country": "United States",
  "status": "Ongoing",
  "voluntaryMandated": "Voluntary: Firm initiated",
  "reportDate": "2026-10-14",
  "recallInitiationDate": "2026-09-10",
  "centerClassificationDate": "2026-10-08",
  "reasonForRecall": "Lack of Assurance of Sterility: Related to formulation using bacteriostic water; Related to processing equipment used in compounded product.",
  "productDescription": "SEMAGLUTIDE/CYANOCOBALAMIN 9/2 MG/ML INJECTABLE, Packaged in single-use dosage syringes, total mL dispensed based on dosage per specific patient prescription, Carolina Infusion LLC, 95 Bees Creek Road, Ridgeland, SC 29936",
  "productQuantity": "82.9 mls - in patient specific syringe dose",
  "codeInfo": "Lot: 07242026@1, BUD: 9/7/2026; 08032026@20, BUD: 9/17/2026; 08312026@16, BUD: 10/15/2026; 08242026@28, BUD: 10/8/2026; 08072026@16, BUD: 9/21/2026. .",
  "distributionPattern": "Nationwide within the U.S",
  "markdownLegalBrief": "# FDA ENFORCEMENT & PRODUCT LIABILITY BRIEF: D-0026-2027\n\n## 1. Executive Risk Summary\n- **Regulatory Domain:** FDA DRUG\n- **Hazard Classification:** Class II (MODERATE / REVERSIBLE HAZARD)\n- **Quantitative Severity Score:** 75/100\n- **Enforcement Status:** Ongoing\n- **Report Date:** 2026-10-14 (Initiated: 2026-09-10)\n\n## 2. Recalling Entity & Jurisdiction\n- **Recalling Firm:** Carolina Infusion, LLC\n- **Location:** Ridgeland, SC (United States)\n- **Action Type:** Voluntary: Firm initiated\n- **Distribution Scope:** Nationwide within the U.S\n\n## 3. Defect & Hazard Analysis\n- **Reason for Recall:** Lack of Assurance of Sterility: Related to formulation using bacteriostic water; Related to processing equipment used in compounded product.\n- **Affected Product Description:** SEMAGLUTIDE/CYANOCOBALAMIN 9/2 MG/ML INJECTABLE, Packaged in single-use dosage syringes, total mL dispensed based on..."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-fda-recalls-safety-monitor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "domain": "drug",
  "classification": "ALL",
  "keyword": "semaglutide",
  "state": "",
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-fda-recalls-safety-monitor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"domain": "drug", "classification": "ALL", "keyword": "semaglutide", "state": "", "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
