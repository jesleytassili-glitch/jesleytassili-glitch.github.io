# US NHTSA Vehicle VIN Decoder & Safety Recall Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/us-nhtsa-vehicle-vin-recall-auditor.html](https://jesleytassili-glitch.github.io/docs/us-nhtsa-vehicle-vin-recall-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/us-nhtsa-vehicle-vin-recall-auditor.md](https://jesleytassili-glitch.github.io/docs/us-nhtsa-vehicle-vin-recall-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/us-nhtsa-vehicle-vin-recall-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/us-nhtsa-vehicle-vin-recall-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/us-nhtsa-vehicle-vin-recall-auditor](https://apify.com/b2b-quant-apis/us-nhtsa-vehicle-vin-recall-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/automotive+%26+vehicle+data/us+nhtsa+vehicle+vin+decoder+safety+recall+api/14664](https://zylalabs.com/api-marketplace/automotive+%26+vehicle+data/us+nhtsa+vehicle+vin+decoder+safety+recall+api/14664)
- **RapidAPI Hub:** [https://rapidapi.com/user/b2bquantapis](https://rapidapi.com/user/b2bquantapis)

## Executive Overview
Batch decode 17-character and partial Vehicle Identification Numbers (VINs), extract official technical specifications, and audit active safety recalls directly from U.S. NHTSA / Department of Transportation APIs.

### Enterprise B2B Value Proposition (US NHTSA Vehicle VIN Decoder & Safety Recall Auditor)
- **Target B2B Buyers:** Auto InsurTechs, Commercial Fleet Managers, Automotive Marketplaces, and Lending Underwriters.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Vehicle VIN Decoded & Recall Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~us-nhtsa-vehicle-vin-recall-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Logistics` | Zyla API Hub `Logistics & Shipping`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** vin-decoder, nhtsa-recalls, vehicle-safety, fleet-management, auto-insurance, automotive-kyb, vpic-api.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `vins` | `array[string]` | Required | List of 17-character Vehicle Identification Numbers to decode and audit. |
| `checkRecalls` | `boolean` | Optional | Query official NHTSA Recall API by decoded Make, Model, and Model Year. |
| `maxResults` | `integer` | Optional | Maximum number of VINs to decode and audit per run. |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `vin` | `string` | VIN |
| `isValidVinFormat` | `boolean` | Valid Format |
| `make` | `string` | Make |
| `model` | `string` | Model |
| `modelYear` | `string` | Model Year |
| `vehicleType` | `string` | Vehicle Type |
| `bodyClass` | `string` | Body Class |
| `engineCylinders` | `string` | Engine Cylinders |
| `displacementL` | `string` | Displacement (L) |
| `fuelTypePrimary` | `string` | Primary Fuel Type |
| `driveType` | `string` | Drive Type |
| `manufacturer` | `string` | Manufacturer |

## Verified Authentic Response Example
```json
{
  "vin": "5UXWX7C5*BA",
  "isValidVinFormat": true,
  "checkDigitValid": false,
  "make": "BMW",
  "model": "X3",
  "modelYear": 2011,
  "vehicleType": "MULTIPURPOSE PASSENGER VEHICLE (MPV)",
  "bodyClass": "Sport Utility Vehicle [SUV]/Multipurpose Vehicle [MPV]",
  "engineCylinders": 6,
  "displacementL": 3.0,
  "fuelTypePrimary": "Gasoline",
  "driveType": "AWD/All-Wheel Drive",
  "manufacturer": "BMW MANUFACTURER CORPORATION / BMW NORTH AMERICA",
  "plantCity": "MUNICH",
  "plantCountry": "GERMANY",
  "errorCode": "6",
  "recallsCount": 4,
  "fleetSafetyStatus": "RECALL_ALERT",
  "recallsSummary": [
    {
      "campaignNumber": "17V683000",
      "component": "ENGINE AND ENGINE COOLING:EXHAUST SYSTEM:EMISSION CONTROL:CRANKCASE (PCV)",
      "summary": "BMW of North America, LLC (BMW) is recalling certain 2008-2011 128i and 2007-2011 328i, 328xi, 328i xDrive, 525i, 525xi, 528i, 528xi, 530i, 530xi, X3 3.0si, X3 xDrive30i, X5 xDrive30i, Z4 3.0i, Z4 3.0si and Z4 sDrive30i vehicles.  The heater for the positive crankcase ventilation (PCV) valve may sho",
      "consequence": "An electrical short can cause the parts within the PCV valve to melt, increasing the risk of a fire, even when the vehicle is not in use.",
      "remedy": "BMW will notify owners, and dealers will replace the PCV valve heater, free of charge.  Interim letters were mailed on November 27, 2017.  Owners will receive a second notification by the end of October 2018.  Owners may contact BMW customer service "
    },
    {
      "campaignNumber": "16V333000",
      "component": "CHILD SEAT:LATCH STRAP",
      "summary": "BMW of North America, LLC (BMW) is recalling certain model year 2011-2017, X3 sDrive28i, X3 xDrive28i and X3 xDrive35i, vehicles manufactured July 2, 2010 to April 14, 2016, 2015-2017 X3 xDrive28d vehicles manufactured March 10, 2014 to March 31, 2016, and 2015-2017 x4 xDrive28i, X4 xDrive35i and X4",
      "consequence": "Damaged lower anchor bars may increase the child's risk of injury in the event of a crash.",
      "remedy": "BMW will notify owners, and dealers will weld a reinforcing bracket to the lower anchor bars and the vehicle body, free of  charge.  The recall began on July 13, 2016.  Owners may contact BMW customer service at 1-800-525-7417."
    },
    {
      "campaignNumber": "11V341000",
      "component": "STEERING:ELECTRIC POWER ASSIST SYSTEM",
      "summary": "BMW IS RECALLING CERTAIN MODEL YEAR 2011 X3 PASSENGER VEHICLES MANUFACTURED FROM APRIL 27, 2011, THROUGH JUNE 8, 2011.  A CONTROL MODULE IN THE ELECTRIC POWER STEERING (EPS) UNIT MAY MALFUNCTION, RESULTING IN A SUDDEN LOSS OF POWER STEERING ASSISTANCE.",
      "consequence": "SUDDEN LOSS OF POWER STEERING ASSISTANCE COULD INCREASE THE RISK OF A CRASH.",
      "remedy": "BMW WILL NOTIFY OWNERS AND DEALERS WILL REPAIR THE VEHICLES FREE OF CHARGE.  THE SAFETY RECALL IS EXPECTED TO BEGIN DURING AUGUST 2011.  OWNERS MAY CONTACT BMW CUSTOMER RELATIONS AND SERVICES AT 1-800-525-7417."
    }
  ],
  "source": "U.S. NHTSA vPIC & Recalls API",
  "auditedAt": "2026-11-03T21:16:52.487645+00:00"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~us-nhtsa-vehicle-vin-recall-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "vins": [
    "5UXWX7C5*BA",
    "1HGCM82633A004352"
  ],
  "checkRecalls": true,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~us-nhtsa-vehicle-vin-recall-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"vins": ["5UXWX7C5*BA", "1HGCM82633A004352"], "checkRecalls": true, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
