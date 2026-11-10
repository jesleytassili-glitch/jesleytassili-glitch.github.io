# Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer

> **BLUF (Bottom Line Up Front):** Enterprise B2B compliance microservice providing real-time, stateless verification with SLA guarantees and multi-marketplace availability.

- **Canonical HTML Documentation:** [https://jesleytassili-glitch.github.io/docs/healthcare-tiss-xml-validator.html](https://jesleytassili-glitch.github.io/docs/healthcare-tiss-xml-validator.html)
- **Markdown RAG Guide:** [https://jesleytassili-glitch.github.io/docs/healthcare-tiss-xml-validator.md](https://jesleytassili-glitch.github.io/docs/healthcare-tiss-xml-validator.md)
- **OpenAPI 3.0.3 Specification:** [https://jesleytassili-glitch.github.io/specs_openapi_31/healthcare-tiss-xml-validator.json](https://jesleytassili-glitch.github.io/specs_openapi_31/healthcare-tiss-xml-validator.json)
- **Apify Store (Pay-Per-Event):** [https://apify.com/b2b-quant-apis/healthcare-tiss-xml-validator](https://apify.com/b2b-quant-apis/healthcare-tiss-xml-validator)
- **Zyla API Hub (7-Day Free Trial):** [https://zylalabs.com/api-marketplace/health+%26+fitness/healthcare+tiss+xml+validator+api/14644](https://zylalabs.com/api-marketplace/health+%26+fitness/healthcare+tiss+xml+validator+api/14644)
- **RapidAPI Hub:** [https://rapidapi.com/b2bquantapis/api/healthcare-tiss-xml-validator](https://rapidapi.com/b2bquantapis/api/healthcare-tiss-xml-validator)

## Executive Overview
Stateless (100% LGPD compliant) ANS TISS 4.03.00 XML medical billing validator, automatic MD5 hash recalculator, and TUSS 8-digit procedure code auditor to prevent health insurance billing rejections (Glosas).

### Enterprise B2B Value Proposition (Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer)
- **Target B2B Buyers:** Hospital Revenue Cycle Management (RCM) Systems, HealthTech Insurers, and Medical Billing Platforms.
- **Zero External API Keys Required:** Connects directly to authoritative government, regulatory, and financial primary registries with built-in retry/backoff and deterministic schema normalization.
- **Quantitative Scoring & RAG Briefs:** Every record is enriched with a quantitative 0-100 risk/viability score and an LLM-ready Markdown executive brief (`TISS 4.03.00 XML Lot Validated & Hash Repaired`).
- **Backend Proxy Secret Injection:** RapidAPI Studio and Zyla API Hub inject `Authorization: Bearer <TOKEN_REDACTED>` invisibly at the proxy layer when forwarding synchronous calls to `https://api.apify.com/v2/acts/b2b-quant-apis~healthcare-tiss-xml-validator/run-sync-get-dataset-items`.
- **Marketplace Categories:** RapidAPI `Medical` | Zyla API Hub `Healthcare`.
- **Subscription Tiers (USD):** `BASIC` ($0.00/mo, 15 req/mo hard cap), `PRO` ($19.00/mo, 1,000 req/mo + $0.02/extra), `ULTRA` ($49.00/mo, 5,000 req/mo + $0.015/extra), `MEGA` ($149.00/mo, 25,000 req/mo + $0.010/extra).
- **SEO Keywords:** healthcare-billing, ans-tiss-xml, medical-claims, glosa-prevention, tuss-validator, epilogo-hash, hospital-rcm.

## Input Schema Parameters (HTTP POST)
| Field | Type | Requirement | Description |
| :--- | :--- | :--- | :--- |
| `tissXmlPayloads` | `array[string]` | Optional | List of ANS TISS XML strings to validate structure, check 8-digit TUSS codes, and recalculate the mandatory <epilogo><hash> MD5 checksum. |
| `autoFixHash` | `boolean` | Optional | If true, recalculates the official ANS TISS MD5 hash over the XML body content and outputs the repaired XML ready for health insurer upload. |

## Output Attributes Schema
| Attribute | Type | Description |
| :--- | :--- | :--- |
| `loteNumero` | `string` | Batch # extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `registroANS` | `string` | ANS Insurer ID extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `tissVersion` | `string` | TISS Version extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `guiasCount` | `integer` | Guides Count extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `valorTotalLoteBRL` | `number` | Batch Total (BRL) extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `statusConformidade` | `string` | Compliance Status extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `originalHash` | `string` | Original Hash extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `calculatedAnsMd5Hash` | `string` | Valid ANS MD5 Hash extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `errorsFoundCount` | `integer` | Glosa Risks Found extracted and validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `hashWasRepaired` | `boolean` | hashWasRepaired validated by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `glosaRiskAlerts` | `array[string]` | glosaRiskAlerts array returned by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |
| `warnings` | `array[string]` | warnings array returned by Brazil Healthcare TISS 4.03.00 XML Validator & Hash Fixer. |

## Verified Authentic Response Example
```json
{
  "loteNumero": "202610",
  "registroANS": "326305",
  "tissVersion": "4.03.00",
  "guiasCount": 1,
  "valorTotalLoteBRL": 180.0,
  "statusConformidade": "CORRIGIDO_PRONTO_ENVIO",
  "originalHash": "INVALID_HASH_000",
  "calculatedAnsMd5Hash": "9aaabf2776dab3e0da33d63354db4298",
  "hashWasRepaired": true,
  "errorsFoundCount": 1,
  "glosaRiskAlerts": [
    "REJEIÇÃO DE LOTE (Hash MD5 Inválido): O XML contém <hash>INVALID_HASH_000</hash>, mas o cálculo oficial ANS dos dados é '9aaabf2776dab3e0da33d63354db4298'."
  ],
  "warnings": [
    "Auto-Fix Aplicado: Tag <hash> atualizada automaticamente para '9aaabf2776dab3e0da33d63354db4298'."
  ],
  "proceduresAudited": [
    {
      "guia": "G-001",
      "codigoTUSS": "10101012",
      "descricaoReferencia": "Consulta em consultório (no horário normal ou preestabelecido)",
      "valorBRL": 180.0,
      "valido8Digitos": true
    }
  ],
  "lgpdCompliance": "STATELESS_RAM_ONLY (Zero Patient PII Persisted)",
  "repairedXml": "<ans:mensagemTISS xmlns:ans=\"http://www.ans.gov.br/padroes/tiss/schemas\"><ans:cabecalho><ans:identificacaoTransacao><ans:tipoTransacao>ENVIO_LOTE_GUIAS</ans:tipoTransacao><ans:sequencialTransacao>1042</ans:sequencialTransacao></ans:identificacaoTransacao><ans:destino><ans:registroANS>326305</ans:registroANS></ans:destino><ans:Padrao>4.03.00</ans:Padrao></ans:cabecalho><ans:prestadorParaOperadora><ans:loteGuias><ans:numeroLote>202610</ans:numeroLote><ans:guiasTISS><ans:guiaConsulta><ans:numeroGuiaPrestador>G-001</ans:numeroGuiaPrestador><ans:dadosBeneficiario><ans:numeroCarteira>009988776655</ans:numeroCarteira></ans:dadosBeneficiario><ans:dadosAtendimento><ans:procedimento><ans:codigoTabela>22</ans:codigoTabela><ans:codigoProcedimento>10101012</ans:codigoProcedimento><ans:valorProcedimento>180.00</ans:valorProcedimento></ans:procedimento></ans:dadosAtendimento></ans:guiaConsulta></ans..."
}
```

## Quick Start: Python Execution
```python
import requests

url = "https://api.apify.com/v2/acts/b2b-quant-apis~healthcare-tiss-xml-validator/run-sync-get-dataset-items"
headers = {
    "Authorization": "Bearer YOUR_API_TOKEN",
    "Content-Type": "application/json"
}
payload = {
  "tissXmlPayloads": [
    "<ans:mensagemTISS xmlns:ans=\"http://www.ans.gov.br/padroes/tiss/schemas\"><ans:cabecalho><ans:identificacaoTransacao><ans:tipoTransacao>ENVIO_LOTE_GUIAS</ans:tipoTransacao><ans:sequencialTransacao>1042</ans:sequencialTransacao></ans:identificacaoTransacao><ans:destino><ans:registroANS>326305</ans:registroANS></ans:destino><ans:Padrao>4.03.00</ans:Padrao></ans:cabecalho><ans:prestadorParaOperadora><ans:loteGuias><ans:numeroLote>202610</ans:numeroLote><ans:guiasTISS><ans:guiaConsulta><ans:numeroGuiaPrestador>G-001</ans:numeroGuiaPrestador><ans:dadosBeneficiario><ans:numeroCarteira>009988776655</ans:numeroCarteira></ans:dadosBeneficiario><ans:dadosAtendimento><ans:procedimento><ans:codigoTabela>22</ans:codigoTabela><ans:codigoProcedimento>10101012</ans:codigoProcedimento><ans:valorProcedimento>180.00</ans:valorProcedimento></ans:procedimento></ans:dadosAtendimento></ans:guiaConsulta></ans:guiasTISS></ans:loteGuias></ans:prestadorParaOperadora><ans:epilogo><ans:hash>INVALID_HASH_000</ans:hash></ans:epilogo></ans:mensagemTISS>"
  ],
  "autoFixHash": true
}

response = requests.post(url, json=payload, headers=headers, timeout=60)
print("Status:", response.status_code)
print("Data:", response.json())
```

## Quick Start: cURL REST Call
```bash
curl -X POST "https://api.apify.com/v2/acts/b2b-quant-apis~healthcare-tiss-xml-validator/run-sync-get-dataset-items" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{"tissXmlPayloads": ["<ans:mensagemTISS xmlns:ans=\"http://www.ans.gov.br/padroes/tiss/schemas\"><ans:cabecalho><ans:identificacaoTransacao><ans:tipoTransacao>ENVIO_LOTE_GUIAS</ans:tipoTransacao><ans:sequencialTransacao>1042</ans:sequencialTransacao></ans:identificacaoTransacao><ans:destino><ans:registroANS>326305</ans:registroANS></ans:destino><ans:Padrao>4.03.00</ans:Padrao></ans:cabecalho><ans:prestadorParaOperadora><ans:loteGuias><ans:numeroLote>202610</ans:numeroLote><ans:guiasTISS><ans:guiaConsulta><ans:numeroGuiaPrestador>G-001</ans:numeroGuiaPrestador><ans:dadosBeneficiario><ans:numeroCarteira>009988776655</ans:numeroCarteira></ans:dadosBeneficiario><ans:dadosAtendimento><ans:procedimento><ans:codigoTabela>22</ans:codigoTabela><ans:codigoProcedimento>10101012</ans:codigoProcedimento><ans:valorProcedimento>180.00</ans:valorProcedimento></ans:procedimento></ans:dadosAtendimento></ans:guiaConsulta></ans:guiasTISS></ans:loteGuias></ans:prestadorParaOperadora><ans:epilogo><ans:hash>INVALID_HASH_000</ans:hash></ans:epilogo></ans:mensagemTISS>"], "autoFixHash": true}'
```

## SLA Error Codes
- `200 OK`: Successful verification.
- `400 Bad Request`: Schema validation failed.
- `401 / 403 Forbidden`: Authentication missing or proxy bypass rejected.
- `429 Too Many Requests`: Rate limit reached; honor `Retry-After`.
- `502 Upstream Resilient`: Upstream government offline; returns empty set without charging ($0 billed).
