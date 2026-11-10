# Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server)

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/b2b-gov-procurement-pncp-radar.html](https://jesleytassili-glitch.github.io/docs/b2b-gov-procurement-pncp-radar.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/b2b-gov-procurement-pncp-radar.md](https://jesleytassili-glitch.github.io/docs/b2b-gov-procurement-pncp-radar.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-gov-procurement-pncp-radar.json](https://jesleytassili-glitch.github.io/specs_openapi_31/b2b-gov-procurement-pncp-radar.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/b2b-gov-procurement-pncp-radar](https://apify.com/b2b-quant-apis/b2b-gov-procurement-pncp-radar)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647](https://zylalabs.com/api-marketplace/legal+%26+compliance/us+sam+gov+federal+procurement+auditor+api/14647)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/b2b-gov-procurement-pncp-radar](https://rapidapi.com/b2bquantapis/api/b2b-gov-procurement-pncp-radar)

## Executive Overview
Extracts, filters, and enriches live Brazilian government public tenders (Pregão Eletrônico, Dispensa - Lei 14.133) from the official PNCP API with item-level pricing, ME/EPP flags, and LLM-ready RAG Markdown briefs.

### Enterprise B2B Value Proposition (Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server))
- **Target B2B Buyers:** GovCon Capture Teams, B2B Sales Intelligence Platforms, and ERP Tender Modules.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Public Tender Analyzed & Enriched`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~b2b-gov-procurement-pncp-radar/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Government & Legal`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** brazil-procurement, pncp, public-tenders, b2g-leads, government-contracts, lei-14133, bidding-radar.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `uf` | `string` | Optional | Two-letter Brazilian state code (e.g., SP, RJ, MG, PR, RS, SC, BA). Leave empty to search nationwide. |
| `keywords` | `array[string]` | Optional | Optional list of keywords to filter tenders by object or item description (case-insensitive, accent-insensitive). Leave empty to return all tenders. |
| `codigoModalidadeContratacao` | `string` | Optional | 6 = Pregão Eletrônico (Most common), 8 = Dispensa de Licitação, 4 = Concorrência Eletrônica. |
| `dataInicial` | `string` | Optional | Publication start date in YYYYMMDD format. If omitted, defaults to 15 days ago. |
| `dataFinal` | `string` | Optional | Publication end date in YYYYMMDD format. If omitted, defaults to today. |
| `maxResults` | `integer` | Optional | Maximum number of matched tenders to output (Pay-Per-Event cap protection). |
| `fetchItems` | `boolean` | Optional | If enabled, queries the PNCP Items API for each matched tender to extract individual items, quantities, unit reference prices, and ME/EPP exclusivity. |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `numeroControlePNCP` | `string` | PNCP ID extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `uf` | `string` | UF extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `municipio` | `string` | City extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `orgaoNome` | `string` | Buyer Organ extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `modalidadeNome` | `string` | Modality extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `valorTotalEstimadoBRL` | `number` | Estimated Value (BRL) extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `viabilityScore` | `integer` | Viability Score (0-100) extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `dataEncerramentoProposta` | `string` | Closing Date extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `objetoCompra` | `string` | Purchase Object extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `linkSistemaOrigem` | `string` | Portal Link extracted and validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `cnpjOrgao` | `string` | cnpjOrgao returned by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |
| `modalidadeId` | `integer` | modalidadeId validated by Brazil Gov Procurement & Bidding Radar (PNCP API + MCP Server). |

## Verified Authentic Response Example
```json
{
  "numeroControlePNCP": "45138088000140-1-000010/2026",
  "cnpjOrgao": "45138088000140",
  "orgaoNome": "MUNICIPIO DE SANTANA DA PONTE PENSA",
  "uf": "SP",
  "municipio": "Santana da Ponte Pensa",
  "modalidadeId": 6,
  "modalidadeNome": "Pregão - Eletrônico",
  "modoDisputaNome": "Aberto",
  "srp": false,
  "valorTotalEstimadoBRL": 286843.24,
  "dataPublicacaoPncp": "2026-10-18T22:11:33",
  "dataAberturaProposta": "2026-10-19T08:00:00",
  "dataEncerramentoProposta": "2026-11-04T08:00:00",
  "objetoCompra": "AQUISIÇÃO DE 01 (UM) VEÍCULO TIPO MINIVAN/VAN, ZERO QUILÔMETRO,\r\nCOM CAPACIDADE PARA 10 (DEZ) PASSAGEIROS E 01 (UM) MOTORISTA,\r\nTOTALIZANDO 11 (ONZE) OCUPANTES, DESTINADO AO TRANSPORTE DE PACIENTES,\r\nACOMPANHANTES E PROFISSIONAIS VINCULADOS À SECRETARIA MUNICIPAL DE\r\nSAÚDE.",
  "informacaoComplementar": null,
  "linkSistemaOrigem": "https://bllcompras.com/Process/ProcessView?param1=[gkz]aI23irKXi8sVBvvGmSdJAcJO9NRjhxFmLuW_Z9mnuAUs9g7pr/3X1ypt4QUIRC2Goe15g9XtyyyZ26pHrUQy17qPgjRPf_GhMJKrwO13McM=",
  "viabilityScore": 85,
  "opportunities": [
    "Faixa de ticket ideal B2B (R$ 286,843.24) com menor concorrência de gigantes."
  ],
  "redFlags": [
    "URGENTE: Encerramento de propostas em menos de 72h (2026-11-04T08:00:00)."
  ],
  "itemsCount": 0,
  "items": [],
  "markdownRagBrief": "# 📋 Raio-X de Licitação PNCP: 45138088000140-1-000010/2026\n- **Órgão Comprador:** MUNICIPIO DE SANTANA DA PONTE PENSA (CNPJ: `45138088000140`)\n- **Localidade:** Santana da Ponte Pensa / SP\n- **Modalidade:** Pregão - Eletrônico | **SRP:** Não\n- **Valor Total Estimado:** R$ 286,843.24\n- **Abertura:** 2026-10-19T08:00:00 | **Encerramento:** 2026-11-04T08:00:00\n- **Score de Viabilidade CRO:** **85/100**\n- **Link Direto:** https://bllcompras.com/Process/ProcessView?param1=[gkz]aI23irKXi8sVBvvGmSdJAcJO9NRjhxFmLuW_Z9mnuAUs9g7pr/3X1ypt4QUIRC2Goe15g9XtyyyZ26pHrUQy17qPgjRPf_GhMJKrwO13McM=\n\n## 🎯 Objeto da Compra\n> AQUISIÇÃO DE 01 (UM) VEÍCULO TIPO MINIVAN/VAN, ZERO QUILÔMETRO,\r\nCOM CAPACIDADE PARA 10 (DEZ) PASSAGEIROS E 01 (UM) MOTORISTA,\r\nTOTALIZANDO 11 (ONZE) OCUPANTES, DESTINADO AO TRANSPORTE DE PACIENTES,\r\nACOMPANHANTES E PROFISSIONAIS VINCULADOS À SECRETARIA MUNICIPAL DE\r\nSAÚDE.\n\n## 🟢 Vanta..."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-gov-procurement-pncp-radar/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "uf": "SP",
  "keywords": [
    "software",
    "cloud",
    "licenciamento"
  ],
  "codigoModalidadeContratacao": "6",
  "dataInicial": "",
  "dataFinal": "",
  "maxResults": 10,
  "fetchItems": false
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~b2b-gov-procurement-pncp-radar/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"uf": "SP", "keywords": ["software", "cloud", "licenciamento"], "codigoModalidadeContratacao": "6", "dataInicial": "", "dataFinal": "", "maxResults": 10, "fetchItems": false}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
