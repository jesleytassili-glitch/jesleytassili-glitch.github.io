# Domain Registration WHOIS, Brand & Antifraud Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/icann-rdap-domain-whois-brand-recon.html](https://jesleytassili-glitch.github.io/docs/icann-rdap-domain-whois-brand-recon.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/icann-rdap-domain-whois-brand-recon.md](https://jesleytassili-glitch.github.io/docs/icann-rdap-domain-whois-brand-recon.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/icann-rdap-domain-whois-brand-recon.json](https://jesleytassili-glitch.github.io/specs_openapi_31/icann-rdap-domain-whois-brand-recon.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/icann-rdap-domain-whois-brand-recon](https://apify.com/b2b-quant-apis/icann-rdap-domain-whois-brand-recon)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646](https://zylalabs.com/api-marketplace/health+%26+fitness/us+fda+recalls+safety+monitor+food+drug+api/14646)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/icann-rdap-domain-whois-brand-recon](https://rapidapi.com/b2bquantapis/api/icann-rdap-domain-whois-brand-recon)

## Executive Overview
Audits corporate and e-commerce domains via official Domain & Verisign WHOIS JSON registries (Zero-Key, replaces paid WHOIS APIs). Extracts registration/expiration dates, registrar, DNSSEC, lock status, and Domain Trust Scores (0-100).

### Enterprise B2B Value Proposition (Domain Registration WHOIS, Brand & Antifraud Auditor)
- **Target B2B Buyers:** Brand Protection Agencies, SOC Threat Hunters, Fraud Prevention Engines, and Domain Registrars.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Domain Registration WHOIS Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~icann-rdap-domain-whois-brand-recon/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Cybersecurity` | Zyla API Hub `Security`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** domain-registration, whois-lookup, domain-age, brand-protection, dnssec-audit, anti-phishing, threat-intelligence.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `domains` | `string` | Required | Comma-separated domain names to audit via official WHOIS (e.g., 'stripe.com,cloudflare.com,shopify.com'). |
| `maxResults` | `integer` | Optional | Maximum number of domains to query and score in a single run (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `domainName` | `string` | ASCII LDH domain name audited. |
| `registryHandle` | `string` | Official registry ROID / Handle. |
| `registrarName` | `string` | Domain-accredited registrar legal name. |
| `registrationDate` | `string` | Original domain registration timestamp (ISO-8601). |
| `expirationDate` | `string` | Upcoming domain expiration timestamp (ISO-8601). |
| `domainAgeYears` | `number` | Domain longevity in years since creation. |
| `transferLocked` | `boolean` | True if clientTransferProhibited or serverTransferProhibited is active. |
| `dnssecSigned` | `boolean` | True if DNSSEC cryptographic signing is enabled. |
| `nameserversCount` | `integer` | Number of authoritative DNS nameservers. |
| `domainTrustScore` | `integer` | Quantitative brand security and antifraud longevity score (0-100). |
| `markdownWhoisBrief` | `string` | Executive Markdown dossier for KYB antifraud, brand protection, and M&A due diligence. |

## Verified Authentic Response Example
```json
{
  "domainName": "stripe.com",
  "registryHandle": "891022_DOMAIN_COM-VRSN",
  "registrarName": "SafeNames Ltd.",
  "registrationDate": "1995-09-12T04:00:00Z",
  "expirationDate": "2027-09-11T04:00:00Z",
  "domainAgeYears": 31.0,
  "transferLocked": true,
  "dnssecSigned": false,
  "nameserversCount": 4,
  "domainTrustScore": 92,
  "markdownWhoisBrief": "# DOMAIN REGISTRATION WHOIS RECON & BRAND SECURITY AUDIT: stripe.com\n\n## 1. Registry & Registrar Identity\n- **Domain Name:** `stripe.com`\n- **Registry Handle (ROID):** `891022_DOMAIN_COM-VRSN`\n- **Accredited Registrar:** **SafeNames Ltd.**\n- **Domain Trust Score:** **92/100**\n\n## 2. Lifecycle Timestamps & Security Posture\n- **Registration Date:** `1995-09-12T04:00:00Z` (Age: **31.0 years**)\n- **Expiration Date:** `2027-09-11T04:00:00Z`\n- **Transfer Lock Protection:** `True`\n- **DNSSEC Delegation Signed:** `False`\n- **Authoritative Nameservers:** `4`"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~icann-rdap-domain-whois-brand-recon/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "domains": "stripe.com,cloudflare.com,shopify.com",
  "maxResults": 5
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~icann-rdap-domain-whois-brand-recon/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"domains": "stripe.com,cloudflare.com,shopify.com", "maxResults": 5}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
