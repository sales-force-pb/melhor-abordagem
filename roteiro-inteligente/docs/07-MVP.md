# 07 - MVP

## Objetivo

Validar se conseguimos transformar uma lista diária de até 10 clientes em um roteiro claramente melhor do que a ordenação manual.

## Escopo do MVP

Entrada:
- 1 responsável;
- ponto inicial;
- até 10 clientes;
- endereço/coordenadas;
- duração estimada de cada visita;
- jornada de trabalho;
- janela de atendimento opcional;
- prioridade opcional.

Processamento:
- normalizar/geocodificar pontos;
- obter matriz de tempo e distância;
- calcular sequência viável;
- respeitar restrições duras;
- otimizar tempo/distância;
- produzir previsão de chegada.

Saída:
- ordem das visitas;
- ETA por cliente;
- tempo de deslocamento por trecho;
- distância por trecho;
- tempo total previsto;
- distância total;
- visitas não encaixadas e motivo.

## Fora do primeiro MVP

- múltiplos vendedores em uma otimização conjunta;
- distribuição automática de clientes entre vendedores;
- aprendizado de duração real das visitas;
- priorização baseada em IA;
- alteração automática por eventos de trânsito em tempo real;
- acompanhamento GPS contínuo;
- navegação turn-by-turn própria.

## Métricas de validação

- redução de quilômetros versus ordem original;
- redução de tempo em trânsito;
- percentual de visitas concluíveis;
- pontualidade em janelas;
- diferença entre ETA e execução real;
- quantidade de replanejamentos.

```mermaid
flowchart LR
    L[Lista de 10 clientes] --> O[Otimizador]
    O --> R[Roteiro]
    R --> M[Medir resultado]
    M --> C[Comparar com roteiro original]
```
