# B2B SSL/TLS CT Log & Subdomain Attack Surface Recon Auditor

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.html](https://jesleytassili-glitch.github.io/docs/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.md](https://jesleytassili-glitch.github.io/docs/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.json](https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor](https://apify.com/b2b-quant-apis/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/security+%26+cybersecurity/b2b+ssl+tls+ct+log+subdomain+attack+surface+api/14666](https://zylalabs.com/api-marketplace/security+%26+cybersecurity/b2b+ssl+tls+ct+log+subdomain+attack+surface+api/14666)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor](https://rapidapi.com/b2bquantapis/api/b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor)

## Executive Overview
Discovers exposed corporate subdomains and SSL/TLS certificates via public Certificate Transparency (CT) logs. Flags wildcard certificates, shadow IT staging/dev endpoints, expiring certs, and computes an Attack Surface Risk Score (0-100).

### Enterprise B2B Value Proposition (B2B SSL/TLS CT Log & Subdomain Attack Surface Recon Auditor)
- **Target B2B Buyers:** External Attack Surface Management (EASM) Platforms, Penetration Testers, Bug Bounty Automation, and SOCs.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`B2B SSL/TLS CT Log Subdomain & Attack Surface Audited`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Cybersecurity` | Zyla API Hub `Security`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** certificate-transparency, subdomain-discovery, attack-surface-management, easm-recon, shadow-it-audit, ssl-tls-monitor, secops-api.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `rootDomain` | `string` | Required | Target corporate domain for External Attack Surface Management (EASM) reconnaissance (e.g., 'apify.com', 'stripe.com', 'cloudflare.com'). |
| `excludeExpired` | `boolean` | Optional | If true, filters strictly for active/non-expired SSL/TLS certificates in Certificate Transparency logs. |
| `maxResults` | `integer` | Optional | Maximum number of CT log subdomain certificates to extract and score (1 to 100). |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `certificateId` | `string` | Public Certificate Transparency (CT) log entry ID. |
| `rootDomain` | `string` | Audited parent domain. |
| `subdomain` | `string` | Subject Alternative Name (SAN) or subdomain discovered in CT logs. |
| `commonName` | `string` | Primary X.509 Common Name. |
| `issuerName` | `string` | Issuing Certificate Authority organization. |
| `notBefore` | `string` | ISO date when certificate validity begins. |
| `notAfter` | `string` | ISO date when certificate expires. |
| `isWildcard` | `boolean` | True if the certificate covers *.domain wildcard scope. |
| `shadowItExposure` | `string` | HIGH_RISK_DEV_STAGING_ADMIN, WILDCARD_BROAD_SCOPE, or STANDARD_PRODUCTION. |
| `attackSurfaceRiskScore` | `integer` | Quantitative EASM & SecOps exposure score (0-100). |
| `markdownSecOpsBrief` | `string` | Executive Markdown advisory for SOC teams, MSSPs, and automated EASM workflows. |

## Verified Authentic Response Example
```json
{
  "certificateId": "30076179807",
  "rootDomain": "cloud.com",
  "subdomain": "verify.cloud.com",
  "commonName": "verify.cloud.com",
  "issuerName": "Let's Encrypt",
  "notBefore": "2026-10-12",
  "notAfter": "2027-01-10",
  "isWildcard": false,
  "shadowItExposure": "STANDARD_PRODUCTION",
  "attackSurfaceRiskScore": 63,
  "markdownSecOpsBrief": "# B2B SSL/TLS CT LOG & ATTACK SURFACE RECON BRIEF: verify.cloud.com\n\n## 1. Subdomain & X.509 Certificate Identity\n- **CT Certificate ID:** `30076179807`\n- **Corporate Root Domain:** `cloud.com`\n- **Discovered Subdomain / SAN:** **`verify.cloud.com`**\n- **Common Name (CN):** `verify.cloud.com`\n- **Issuing Certificate Authority:** Let's Encrypt\n\n## 2. EASM Exposure Classification & Validity\n- **Attack Surface Risk Score:** **63/100**\n- **Exposure Classification:** **`STANDARD_PRODUCTION`**\n- **Wildcard Scope (`*.domain`):** `False`\n- **Valid From (`notBefore`):** `2026-10-12`\n- **Expires On (`notAfter`):** `2027-01-10`"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "rootDomain": "cloudflare.com",
  "excludeExpired": true,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-ssl-tls-ct-log-subdomain-attack-surface-auditor/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"rootDomain": "cloudflare.com", "excludeExpired": true, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
