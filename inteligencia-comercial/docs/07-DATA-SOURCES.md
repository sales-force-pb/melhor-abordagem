# 07 - Fontes de Dados

## Objetivo
Catalogar categorias de fontes necessárias para produzir inteligência comercial rastreável. A inclusão neste documento não significa que um provider já foi contratado ou tecnicamente aprovado.

## Categorias

### Localização e mapas
Possíveis usos: reverse geocoding, endereço normalizado, estabelecimentos próximos, categorias comerciais, distância e contexto geográfico.

### Dados empresariais oficiais
Possíveis usos: razão social, nome fantasia, situação cadastral, CNAE, data de abertura e informações societárias empresariais permitidas.

### Dados estatísticos e territoriais
Possíveis usos: população, características territoriais, indicadores socioeconômicos agregados e contexto regional.

### Presença digital comercial
Possíveis usos: site oficial, perfis comerciais, canais de contato, frequência de publicação e sinais públicos de atividade empresarial.

### Reputação pública
Possíveis usos: avaliações, volume de avaliações, temas recorrentes, sinais positivos e pontos de atrito.

### Evidência histórica
Possíveis usos: registros públicos datados, imagens históricas permitidas, avaliações antigas e outras evidências capazes de sustentar uma estimativa de presença no endereço.

### Indicadores econômicos e de mercado
Possíveis usos: estatísticas agregadas do segmento, dinâmica regional, oferta, demanda e indicadores autorizados de risco.

## Critérios de aprovação de uma fonte
Cada provider deverá ser avaliado por:

- legalidade e termos de uso;
- finalidade permitida;
- qualidade e atualização;
- cobertura geográfica;
- custo;
- rate limit;
- disponibilidade/SLA;
- capacidade de citar a origem;
- política de retenção;
- possibilidade de cache;
- tratamento de dados pessoais.

## Proveniência
Todo dado utilizado na conclusão deve permitir registrar sua origem.

```mermaid
flowchart LR
    S[Source] --> C[Collector]
    C --> N[Normalization]
    N --> E[Evidence]
    E --> F[Fact or Inference]
    F --> R[Final Report]
```

## Regra
Scraping não autorizado ou coleta indiscriminada de dados pessoais não será tratado como estratégia padrão do produto. Providers e fontes serão aprovados explicitamente antes da implementação.
