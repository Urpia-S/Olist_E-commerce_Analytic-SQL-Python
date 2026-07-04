# Resumo inicial dos resultados

Este arquivo registra uma leitura inicial dos CSVs exportados.

## Visao geral

| Metrica                                      |         Valor |
|----------------------------------------------|--------------:|
| Pedidos totais                               |        99.441 |
| Pedidos entregues                            |        96.478 |
| Receita de produtos                          | 13.591.643,70 |
| Ticket medio de produtos por pedido          |        136,68 |
| Tempo medio de entrega                       |    12,50 dias |
| Percentual de atraso entre pedidos entregues |         6,77% |
| Nota media geral dos reviews                 |          4,09 |

## Categorias com maior receita

As cinco primeiras categorias em `outputs/receita_por_categoria.csv` foram:

| Categoria               | Receita de produtos | Pedidos |
|-------------------------|--------------------:|--------:|
| `health_beauty`         |        1.258.681,34 |   8.836 |
| `watches_gifts`         |        1.205.005,68 |   5.624 |
| `bed_bath_table`        |        1.036.988,68 |   9.417 |
| `sports_leisure`        |          988.048,97 |   7.720 |
| `computers_accessories` |          911.954,32 |   6.689 |

## Entrega e atraso

Os estados com maior percentual de atraso no arquivo `outputs/indicadores_entrega_estado.csv` foram:

| Estado | Pedidos | Media de dias de entrega | Percentual de atraso |
|--------|--------:|-------------------------:|---------------------:|
| AL     |     413 |                    24,50 |               21,41% |
| MA     |     747 |                    21,51 |               17,43% |
| SE     |     350 |                    21,46 |               15,22% |
| PI     |     495 |                    19,39 |               13,87% |
| CE     |   1.336 |                    21,20 |               13,76% |

Isso sugere que a distancia/logistica regional tem papel importante no risco de atraso.

## Satisfacao e prazo

O arquivo `outputs/satisfacao_por_status_entrega.csv` mostra uma diferenca forte:

| Status da entrega      | Pedidos | Nota media | Reviews baixos |
|------------------------|--------:|-----------:|---------------:|
| Sem entrega confirmada |   2.965 |       1,75 |         77,66% |
| Atrasada               |   6.535 |       2,27 |         62,40% |
| No prazo               |  89.941 |       4,29 |          9,28% |

Essa e uma das conclusoes mais importantes do projeto: atraso e ausencia de entrega confirmada estao fortemente associados a notas piores.

## Recompra

O arquivo `outputs/clientes_recorrencia.csv` indica:

| Tipo de cliente | Clientes | Percentual |
|-----------------|---------:|-----------:|
| Compra unica    |   93.099 |     96,88% |
| Recorrente      |    2.997 |      3,12% |

A base e majoritariamente de compra unica. Por isso, a segmentacao RFM e util para separar clientes recentes, clientes de alto valor e clientes inativos, mesmo quando a recorrencia geral e baixa.

## Cuidados metodologicos

Ao calcular valores financeiros, o projeto evita unir itens e pagamentos diretamente na mesma granularidade sem agregacao previa.

Esse cuidado e importante porque um pedido pode ter:

-   varios itens;
-   mais de uma linha de pagamento.

Se as duas tabelas forem unidas diretamente, os valores podem ser multiplicados. Por isso, o script agrega itens e pagamentos por pedido antes de calcular metricas de cliente ou pedido.
