# ADR-002 - Evidence First

- **Status:** Aceito como princípio do produto
- **Data:** 2026-08-17

## Contexto
O produto utilizará IA e múltiplas fontes externas. Sem proveniência, inferências podem ser confundidas com fatos e reduzir a confiabilidade do resultado.

## Decisão
Adotar `Evidence First` como princípio arquitetural: findings relevantes devem ser sustentados por evidências rastreáveis e classificados quanto à natureza da informação.

## Regras
- fato e inferência são conceitos diferentes;
- fonte e data devem ser preservadas quando disponíveis;
- confidence deve considerar qualidade e concordância das evidências;
- LLM não é fonte factual;
- ausência de evidência deve reduzir confidence ou impedir determinada afirmação;
- o relatório final deve comunicar incerteza.

## Consequências
O modelo de dados, agentes, contratos e observabilidade deverão preservar proveniência desde a coleta até a consolidação final.
