# Brazil B2B CNPJ, Partners (QSA) & CNAE Lead Enricher

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/brazil-b2b-cnpj-qsa-lead-enricher.html](https://jesleytassili-glitch.github.io/docs/brazil-b2b-cnpj-qsa-lead-enricher.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/brazil-b2b-cnpj-qsa-lead-enricher.md](https://jesleytassili-glitch.github.io/docs/brazil-b2b-cnpj-qsa-lead-enricher.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-b2b-cnpj-qsa-lead-enricher.json](https://jesleytassili-glitch.github.io/specs_openapi_31/brazil-b2b-cnpj-qsa-lead-enricher.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/brazil-b2b-cnpj-qsa-lead-enricher](https://apify.com/b2b-quant-apis/brazil-b2b-cnpj-qsa-lead-enricher)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645](https://zylalabs.com/api-marketplace/travel+%26+transportation/brazil+antt+minimum+freight+calculator+ct+e+api/14645)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/brazil-b2b-cnpj-qsa-lead-enricher](https://rapidapi.com/b2bquantapis/api/brazil-b2b-cnpj-qsa-lead-enricher)

## Executive Overview
Mathematical Modulo 11 validator and batch B2B company lead enricher for Brazilian CNPJs via Brazilian federal corporate registries. Extracts Razao Social, Nome Fantasia, Situacao Cadastral, CNAEs, Capital Social, Simples Nacional/MEI status, partners (QSA), and contact details.

### Enterprise B2B Value Proposition (Brazil B2B CNPJ, Partners (QSA) & CNAE Lead Enricher)
- **Target B2B Buyers:** FinTech KYB Onboarding Flows, B2B Credit Bureaus, and Enterprise CRM Enrichment Pipelines.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`Brazilian CNPJ & Partners (QSA) Lead Enriched`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~brazil-b2b-cnpj-qsa-lead-enricher/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Business` | Zyla API Hub `Company Data`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** cnpj-lookup, receita-federal, qsa-ubo-partners, brazil-kyb, company-enrichment, cnae-lookup, b2b-credit-risk.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `cnpjs` | `array[string]` | Required | List of Brazilian CNPJ numbers to validate and enrich. |
| `includeSecondaryCnaes` | `boolean` | Optional | Include all secondary economic activities (CNAEs Secundários) in the output record and markdown dossier. |
| `timeoutSeconds` | `integer` | Optional | HTTP timeout in seconds for each API request to Brazilian federal corporate registries. |
| `maxResults` | `integer` | Optional | Maximum number of CNPJ records to process in a single execution. |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `cnpj` | `string` | 14-digit unformatted CNPJ identifier. |
| `cnpjFormatted` | `string` | Formatted CNPJ (XX.XXX.XXX/XXXX-XX). |
| `isValidMod11` | `boolean` | Whether the CNPJ passed Modulo 11 check-digit validation. |
| `status` | `string` | Enrichment status (ENRICHED, INVALID_MOD11, NOT_FOUND, API_ERROR). |
| `dataSource` | `string` | Primary source of enrichment (Brazilian federal corporate registry, Brazilian corporate registry, FallbackCache, LOCAL_MOD11_VALIDATOR). |
| `razaoSocial` | `string` | Official corporate legal name (Razão Social). |
| `nomeFantasia` | `string` | Trade name (Nome Fantasia). |
| `situacaoCadastral` | `string` | Registration status at Receita Federal (e.g. ATIVA, BAIXADA, INAPTA). |
| `cnaePrincipalCodigo` | `string` | Primary economic activity code (CNAE Fiscal). |
| `cnaePrincipalDescricao` | `string` | Primary economic activity description. |
| `capitalSocialBRL` | `number` | Registered share capital in BRL (Capital Social). |
| `opcaoPeloSimples` | `boolean` | Whether the company is opted into Simples Nacional tax regime. |

## Verified Authentic Response Example
```json
{
  "cnpj": "00000000000191",
  "cnpjFormatted": "00.000.000/0001-91",
  "isValidMod11": true,
  "status": "ENRICHED",
  "dataSource": "Brazilian federal CNPJ public registry",
  "razaoSocial": "BANCO DO BRASIL SA",
  "nomeFantasia": "DIRECAO GERAL",
  "situacaoCadastral": "ATIVA",
  "dataInicioAtividade": "1966-08-01",
  "porte": "DEMAIS",
  "naturezaJuridica": "Sociedade de Economia Mista",
  "capitalSocialBRL": 120000000000.0,
  "cnaePrincipalCodigo": "6422100",
  "cnaePrincipalDescricao": "Bancos múltiplos, com carteira comercial",
  "cnaesSecundarios": [
    {
      "codigo": "6499999",
      "descricao": "Outras atividades de serviços financeiros não especificadas anteriormente"
    }
  ],
  "opcaoPeloSimples": false,
  "dataOpcaoPeloSimples": "2007-07-01",
  "opcaoPeloMei": false,
  "uf": "DF",
  "municipio": "BRASILIA",
  "logradouro": "SAUN QUADRA 5 BLOCO B TORRE I, II, III",
  "numero": "SN",
  "complemento": "ANDAR T I SL S101 A S1602 T II SL C101 A C1602 TIII SL N101 A N1602",
  "bairro": "ASA NORTE",
  "cep": "70040912",
  "telefonePublico": "6134939002",
  "emailPublico": null,
  "sociosCount": 41,
  "qsa": [
    {
      "nomeSocio": "ALAN CARLOS GUEDES DE OLIVEIRA",
      "qualificacaoSocio": "Diretor",
      "faixaEtaria": "Entre 41 a 50 anos",
      "dataEntradaSociedade": "2023-05-17",
      "identificadorDeSocio": "2",
      "cnpjCpfDoSocio": "***550179**"
    },
    {
      "nomeSocio": "ALBERTO MARTINHAGO VIEIRA",
      "qualificacaoSocio": "Diretor",
      "faixaEtaria": "Entre 41 a 50 anos",
      "dataEntradaSociedade": "2023-07-20",
      "identificadorDeSocio": "2",
      "cnpjCpfDoSocio": "***842999**"
    },
    {
      "nomeSocio": "ALEXANDRE BOCCHETTI NUNES",
      "qualificacaoSocio": "Diretor",
      "faixaEtaria": "Entre 51 a 60 anos",
      "dataEntradaSociedade": "2025-08-28",
      "identificadorDeSocio": "2",
      "cnpjCpfDoSocio": "***753277**"
    }
  ],
  "enrichedAt": "2026-11-03T21:16:52.999962+00:00",
  "markdownCompanyDossier": "# Dossiê Corporativo B2B — BANCO DO BRASIL SA (00.000.000/0001-91)\n\n## 1. Identificação Cadastral e Tributária\n- **CNPJ:** `00.000.000/0001-91` (Módulo 11: `VÁLIDO`)\n- **Razão Social:** BANCO DO BRASIL SA\n- **Nome Fantasia:** DIRECAO GERAL\n- **Situação Cadastral:** `ATIVA`\n- **Data de Abertura:** 1966-08-01\n- **Porte / Natureza Jurídica:** DEMAIS | Sociedade de Economia Mista\n- **Capital Social:** R$ 120,000,000,000.00\n- **Optante pelo Simples Nacional:** Não\n- **Enquadrado como MEI:** Não\n- **Fonte Primária dos Dados:** `Brazilian federal CNPJ public registry`\n\n## 2. Atividade Econômica (CNAE)\n- **CNAE Principal:** `6422100` — Bancos múltiplos, com carteira comercial\n- **CNAEs Secundários (1):**\n  - `6499999`: Outras atividades de serviços financeiros não especificadas anteriormente\n\n## 3. Localização e Contatos Públicos\n- **Município / UF:** BRASILIA / DF\n- **Endereço Registrado:** SAU... [truncated for preview]"
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-b2b-cnpj-qsa-lead-enricher/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "cnpjs": [
    "00.000.000/0001-91",
    "33.000.167/0001-01"
  ],
  "includeSecondaryCnaes": true,
  "timeoutSeconds": 15,
  "maxResults": 10
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~brazil-b2b-cnpj-qsa-lead-enricher/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"cnpjs": ["00.000.000/0001-91", "33.000.167/0001-01"], "includeSecondaryCnaes": true, "timeoutSeconds": 15, "maxResults": 10}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
