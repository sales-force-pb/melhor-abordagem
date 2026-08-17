# ADR-001 - Arquitetura Orientada a Eventos

- **Status:** Proposto
- **Data:** 2026-08-17

## Contexto
A análise de um estabelecimento envolve tarefas independentes, fontes externas com latências diferentes e possibilidade de execução paralela.

## Decisão
Adotar arquitetura orientada a eventos para coordenar os componentes de análise. RabbitMQ é a tecnologia inicialmente escolhida para mensageria, sujeita a validação durante a fase técnica.

## Consequências positivas
- desacoplamento;
- paralelismo;
- retry isolado;
- escalabilidade por consumidor;
- rastreabilidade do workflow;
- possibilidade de reprocessamento parcial.

## Trade-offs
- consistência eventual;
- maior complexidade operacional;
- necessidade de idempotência;
- versionamento de eventos;
- tratamento explícito de mensagens duplicadas e DLQ.

## Observação
Este ADR registra uma decisão de arquitetura conceitual. Parâmetros concretos de exchanges, filas e infraestrutura serão definidos posteriormente.
