# 09 - Contrato Conceitual da API

## Objetivo
Definir a fronteira externa do produto antes de escolher detalhes de implementação.

## Criar análise
`POST /analyses`

Entrada conceitual:
```json
{
  "image": {
    "content": "base64-or-reference",
    "mimeType": "image/jpeg"
  },
  "location": {
    "latitude": -8.0,
    "longitude": -34.0,
    "accuracyMeters": 10
  }
}
```

Resposta assíncrona:
```json
{
  "analysisId": "uuid",
  "status": "REQUESTED",
  "createdAt": "ISO-8601"
}
```

## Consultar análise
`GET /analyses/{analysisId}`

Estados previstos:
- `REQUESTED`
- `RUNNING`
- `PARTIAL`
- `COMPLETED`
- `FAILED`

## Consultar componentes
`GET /analyses/{analysisId}/components`

Permite compreender quais dimensões foram concluídas, falharam ou permanecem em processamento.

## Consultar evidências
`GET /analyses/{analysisId}/evidence`

A exposição pública das evidências dependerá de autorização e política de segurança, mas o domínio deve suportar rastreabilidade desde o início.

## Resultado
O resultado final deverá separar claramente:

- identidade do estabelecimento;
- dados empresariais;
- perfil do negócio;
- mercado e região;
- concorrência;
- presença digital;
- histórico estimado;
- findings;
- confidence;
- cobertura da análise;
- fontes/evidências permitidas.

## Idempotência
A API deverá prever uma estratégia de idempotency key para impedir análises duplicadas causadas por retries do cliente.

## Versionamento
Contratos externos serão versionados. A estratégia exata (`/v1`, header ou media type) será decidida em ADR antes da implementação.
