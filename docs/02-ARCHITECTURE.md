# 02 — Arquitetura Conceitual

## Objetivo

Este documento descreve a arquitetura conceitual inicial. Ele não define ainda bibliotecas, versões ou detalhes de implementação.

## Princípios

A arquitetura deverá favorecer:

- processamento assíncrono;
- baixo acoplamento entre capacidades;
- agentes especializados;
- execução paralela quando possível;
- retry independente;
- rastreabilidade ponta a ponta;
- idempotência;
- observabilidade;
- evolução incremental;
- controle de custo de IA e APIs externas.

## Visão de componentes

```mermaid
flowchart TB
    Input[Foto + Geolocalização]
    API[API / Analysis Orchestrator]
    MQ[(RabbitMQ)]
    State[(Analysis State)]
    Evidence[(Evidence Repository)]

    subgraph Identification
        Vision[Vision Agent]
        Location[Location Agent]
        Resolver[Entity Resolution]
    end

    subgraph Enrichment
        Company[Company Enrichment]
        History[Historical Presence]
        Social[Digital Presence]
        Reputation[Reputation]
    end

    subgraph Market
        Competition[Competition]
        Audience[Audience]
        Demand[Market Demand]
        Risk[Economic Risk]
    end

    Intelligence[Intelligence Consolidation]
    Output[Dossiê]

    Input --> API
    API --> State
    API --> MQ

    MQ --> Vision
    MQ --> Location
    Vision --> Resolver
    Location --> Resolver

    Resolver --> MQ

    MQ --> Company
    MQ --> History
    MQ --> Social
    MQ --> Reputation
    MQ --> Competition
    MQ --> Audience
    MQ --> Demand
    MQ --> Risk

    Company --> Evidence
    History --> Evidence
    Social --> Evidence
    Reputation --> Evidence
    Competition --> Evidence
    Audience --> Evidence
    Demand --> Evidence
    Risk --> Evidence

    Evidence --> Intelligence
    Intelligence --> Output
    Output --> State
```

## Por que orientação a eventos

Algumas pesquisas podem ser independentes entre si e possuir tempos, custos e probabilidades de falha diferentes.

A mensageria permite que cada capacidade:

- seja executada separadamente;
- seja reprocessada sem reiniciar toda a análise;
- possua políticas próprias de retry;
- seja substituída futuramente;
- escale de forma independente;
- utilize modelos de IA diferentes.

## Fluxo conceitual de eventos

```mermaid
sequenceDiagram
    participant C as Cliente
    participant API as Analysis API
    participant MQ as RabbitMQ
    participant V as Vision Agent
    participant L as Location Agent
    participant R as Entity Resolver
    participant E as Enrichment Agents
    participant I as Intelligence Agent

    C->>API: foto + geolocalização
    API->>MQ: analysis.requested
    MQ-->>V: vision.requested
    MQ-->>L: location.requested
    V-->>MQ: vision.completed
    L-->>MQ: location.completed
    MQ-->>R: entity-resolution.requested
    R-->>MQ: establishment.identified
    MQ-->>E: enrichment requests
    E-->>MQ: enrichment results
    MQ-->>I: intelligence.requested
    I-->>API: analysis.completed
    API-->>C: dossiê disponível
```

## Java e IA

A visão atual é utilizar Java como cérebro operacional da plataforma: contratos, workflow, estado, mensageria, segurança, persistência, auditoria e observabilidade.

Os agentes de IA são capacidades especializadas dentro desse ecossistema. A arquitetura não deverá assumir que todo processamento exige um LLM.

Sempre que uma informação puder ser obtida deterministicamente por API, banco ou regra, essa alternativa deverá ser considerada antes de utilizar IA generativa.

## Decisões ainda abertas

Ainda serão definidos em documentos/ADRs futuros:

- versão do Java;
- versão do Spring Boot;
- estratégia de orquestração;
- topologia RabbitMQ;
- persistência principal;
- armazenamento das imagens;
- cache;
- provedores de IA;
- APIs externas;
- modelo de observabilidade;
- política de custos.
