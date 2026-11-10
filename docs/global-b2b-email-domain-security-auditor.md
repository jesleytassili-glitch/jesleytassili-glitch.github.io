# Global B2B Email, MX, SPF & DMARC Deliverability Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/global-b2b-email-domain-security-auditor.html](https://jesleytassili-glitch.github.io/docs/global-b2b-email-domain-security-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/global-b2b-email-domain-security-auditor.md](https://jesleytassili-glitch.github.io/docs/global-b2b-email-domain-security-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/global-b2b-email-domain-security-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/global-b2b-email-domain-security-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/global-b2b-email-domain-security-auditor](https://apify.com/b2b-quant-apis/global-b2b-email-domain-security-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646](https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/global-b2b-email-domain-security-auditor](https://rapidapi.com/b2bquantapis/api/global-b2b-email-domain-security-auditor)

## Executive Overview
High-speed asynchronous B2B email and corporate domain auditor via DNS-over-HTTPS (Cloudflare & Google DNS). Validates RFC 5322 syntax, disposable domains, MX records, email provider (Google Workspace, Microsoft 365, Proofpoint, Mimecast), SPF, and DMARC policies.

### Enterprise B2B Value Proposition (Global B2B Email, MX, SPF & DMARC Deliverability Auditor)
- **Target B2B Buyers:** B2B Outbound Platforms, FinTech Onboarding Anti-Fraud Engines, and SOC Security Teams.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`B2B Email / Corporate Domain Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~global-b2b-email-domain-security-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Cybersecurity` | Zyla API Hub `Security`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** email-verification, dmarc-spf-mx, domain-security, disposable-email, kyb-fraud-prevention, b2b-lead-hygiene, secops.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `targets` | `array[string]` | Required | List of email addresses or domain names to audit |
| `checkDmarcAndSpf` | `boolean` | Optional | Query TXT records for SPF and _dmarc policies |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `inputTarget` | `string` | Original email address or domain submitted for audit |
| `domain` | `string` | Extracted and normalized domain name |
| `isValidSyntax` | `boolean` | Whether the input satisfies RFC 5322 email or DNS hostname syntax |
| `isDisposable` | `boolean` | Whether the domain belongs to a known temporary/disposable email provider |
| `isRoleAccount` | `boolean` | Whether the email local-part is a generic role address (sales@, admin@, support@, etc.) |
| `hasMxRecords` | `boolean` | Whether the domain has active Mail Exchange (MX) DNS records |
| `emailProvider` | `string` | Detected B2B email provider or gateway from MX records |
| `hasSpf` | `boolean` | Whether the domain publishes a valid v=spf1 TXT policy |
| `hasDmarc` | `boolean` | Whether _dmarc.<domain> publishes a valid v=DMARC1 TXT policy |
| `dmarcPolicy` | `string` | Extracted DMARC enforcement policy (reject, quarantine, none, missing, or skipped) |
| `deliverabilityScore` | `integer` | Composite B2B deliverability and domain security score (0-100) |
| `statusVerdict` | `string` | Final audit verdict classification |

## Verified Authentic Response Example
```json
{
  "inputTarget": "contact@openai.com",
  "domain": "openai.com",
  "isValidSyntax": true,
  "isDisposable": false,
  "isRoleAccount": true,
  "roleAccount": true,
  "hasMxRecords": true,
  "emailProvider": "Google Workspace",
  "mxRecords": [
    "aspmx.l.google.com",
    "alt1.aspmx.l.google.com",
    "alt2.aspmx.l.google.com"
  ],
  "hasSpf": true,
  "spfRecord": "v=spf1 include:_spf.google.com include:spf.protection.outlook.com include:8050860.spf04.hubspotemail.net include:mktomail.com include:spf_c.oraclecloud.com -all",
  "hasDmarc": true,
  "dmarcPolicy": "reject",
  "dmarcRecord": "v=DMARC1; p=reject; rua=mailto:tdfyvl0n@ag.dmarcian.com; ruf=mailto:tdfyvl0n@fr.dmarcian.com; fo=1; aspf=r",
  "deliverabilityScore": 95,
  "statusVerdict": "DELIVERABLE_HIGH_TRUST",
  "auditedAt": "2026-11-03T21:16:49.682059+00:00"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~global-b2b-email-domain-security-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "targets": [
    "contact@openai.com",
    "sales@stripe.com",
    "fake@mailinator.com"
  ],
  "checkDmarcAndSpf": true
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~global-b2b-email-domain-security-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"targets": ["contact@openai.com", "sales@stripe.com", "fake@mailinator.com"], "checkDmarcAndSpf": true}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
