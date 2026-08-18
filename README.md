# Melhor Abordagem

Repositório de concepção funcional e arquitetural para iniciativas voltadas à melhoria da atuação comercial em campo.

> **Status atual:** documentação e diagramas. Ainda não existem implementações executáveis.

## Iniciativas

### 1. Inteligência Comercial

Identificação e enriquecimento de estabelecimentos a partir de foto da fachada e geolocalização, combinando dados empresariais, mercado, concorrência, presença digital e evidências para produzir um dossiê comercial rastreável.

➡️ [Acessar documentação de Inteligência Comercial](inteligencia-comercial/README.md)

```mermaid
flowchart LR
    A[Foto + Geolocalização]
    B[Identificação]
    C[Inteligência Comercial]
    D[Evidências]
    E[Dossiê]
    A --> B
    B --> C
    C --> D
    D --> E
```

### 2. Roteiro Inteligente

Planejamento diário da melhor sequência para uma pessoa visitar até 10 clientes, considerando deslocamento real, tempo, distância, janelas de atendimento, duração das visitas e restrições operacionais.

➡️ [Acessar documentação de Roteiro Inteligente](roteiro-inteligente/README.md)

```mermaid
flowchart LR
    A[10 clientes do dia]
    B[Geocodificação]
    C[Matriz de tempo e distância]
    D[Regras e janelas]
    E[Route Optimizer]
    F[Roteiro diário]
    A --> B
    B --> C
    A --> D
    C --> E
    D --> E
    E --> F
```

## Relação entre as iniciativas

As iniciativas são independentes, mas podem se complementar no futuro. A Inteligência Comercial pode ajudar a determinar **quem merece prioridade**, enquanto o Roteiro Inteligente decide **em qual ordem visitar os clientes selecionados**.

```mermaid
flowchart LR
    IC[Inteligência Comercial]
    P[Prioridade / Contexto do cliente]
    RI[Roteiro Inteligente]
    R[Visitas priorizadas e ordenadas]
    IC --> P
    P --> RI
    RI --> R
```

## Estrutura

```text
melhor-abordagem/
├── README.md
├── inteligencia-comercial/
│   ├── README.md
│   └── docs/
│       └── ADR/
└── roteiro-inteligente/
    ├── README.md
    └── docs/
```

## Diretriz atual

Por enquanto, o trabalho permanece exclusivamente em documentação funcional, arquitetura, modelos de domínio, contratos conceituais, diagramas Mermaid, decisões de arquitetura e definição de MVPs.
