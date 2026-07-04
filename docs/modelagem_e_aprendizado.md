# Modelagem e aprendizado SQL

Este documento explica as principais decisoes de modelagem do projeto.

## Por que existe uma camada staging?

Arquivos CSV podem ter campos vazios, datas em texto, numeros como texto e pequenas inconsistencias. Por isso, a camada `staging` importa quase tudo como `text`.

Esse padrao ajuda a separar dois problemas:

-   primeiro, verificar se o arquivo entrou no banco;
-   depois, converter tipos e aplicar regras relacionais.

Exemplo:

``` sql
NULLIF(order_purchase_timestamp, '')::timestamp AS order_purchase_timestamp
```

Aqui acontecem duas coisas:

-   `NULLIF(campo, '')` transforma string vazia em `NULL`;
-   `::timestamp` converte o texto para data e hora do PostgreSQL.

## Camada core

A camada `core` representa o modelo relacional do projeto. Ela tem:

-   chaves primarias;
-   chaves estrangeiras;
-   tipos corretos para datas e numeros;
-   indices em colunas usadas em joins e filtros.

## Principais tabelas

| Tabela | Papel |
|------------------------------------|------------------------------------|
| `core.customers` | Clientes e localizacao do comprador. |
| `core.orders` | Pedido, status e datas do funil de entrega. |
| `core.order_items` | Itens de cada pedido, produto, vendedor, preco e frete. |
| `core.order_payments` | Pagamentos por pedido. |
| `core.order_reviews` | Avaliacoes dos clientes. |
| `core.products` | Produtos e atributos fisicos. |
| `core.sellers` | Vendedores e estados. |
| `core.product_category_translation` | Traducao de categoria para ingles. |

## Views analiticas

Este projeto usa views para:

-   somar receita e frete por pedido;
-   calcular variaveis de entrega;
-   agregar reviews por pedido;
-   enriquecer itens com categoria traduzida, estado do cliente e estado do vendedor.

## Variaveis de entrega

As variaveis abaixo ficam em `analytics.vw_order_delivery`:

| Variavel | Significado |
|------------------------------------|------------------------------------|
| `dias_entrega` | Dias entre compra e entrega ao cliente. |
| `dias_ate_aprovacao` | Dias entre compra e aprovacao. |
| `dias_ate_transportadora` | Dias entre aprovacao e envio para transportadora. |
| `dias_transporte_cliente` | Dias entre transportadora e cliente. |
| `dias_atraso` | Dias de atraso em relacao a data estimada. |
| `entrega_atrasada` | Verdadeiro quando a entrega passou da data estimada. |

## Segmentacao RFM

-   **Recencia**: quanto tempo faz desde a ultima compra;
-   **Frequencia**: quantos pedidos o cliente fez;
-   **Valor**: quanto o cliente gastou.

O projeto usa `NTILE(5)` para transformar cada dimensao em notas de 1 a 5.

``` sql
NTILE(5) OVER (ORDER BY recencia_dias DESC) AS score_recencia
```

Para recencia, clientes com menor quantidade de dias desde a ultima compra recebem score maior.

O script tambem usa `RANK` e `DENSE_RANK` como exemplos de funcoes de janela, mantendo a implementacao diferente do notebook de referencia.

## Ajustes de outrso bancos de dados para o SQLite

| Ideia                | SQLite                               |
|----------------------|--------------------------------------|
| Mes da data          | `STRFTIME('%Y-%m', data)`            |
| Diferenca de datas   | `JULIANDAY(fim) - JULIANDAY(inicio)` |
| Data sem hora        | `DATE(data)`                         |
| Texto em `CASE WHEN` | as vezes aparece com aspas duplas    |
