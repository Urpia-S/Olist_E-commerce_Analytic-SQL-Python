# Olist E-commerce Analytics - SQL + Python

Projeto de analise de e-commerce com a base publica da Olist, organizado principalmente em notebooks para Google Colab.

## Como executar

A forma recomendada e abrir os notebooks no Google Colab.

Execute primeiro o notebook `01`, que prepara a base SQLite usada pelos demais notebooks. Depois rode os notebooks analiticos por tema.

| Ordem | Notebook                                  |
|------:|-------------------------------------------|
|     1 | `01_preparacao_base_colab.ipynb`          |
|     2 | `02_temporal_receita_colab.ipynb`         |
|     3 | `03_entregas_satisfacao_colab.ipynb`      |
|     4 | `04_rfm_retencao_colab.ipynb`             |
|     5 | `05_afinidade_vendedores_colab.ipynb`     |
|     6 | `06_playground_consultas_sql_colab.ipynb` |

## Dados

Os CSVs brutos da Olist nao ficam versionados no repositorio, porque sao arquivos grandes.

Para que os notebooks funcionem para qualquer pessoa que abrir pelo GitHub, publiquei uma Release chamada `data-v1` neste repositorio:

[Release data-v1](https://github.com/Urpia-S/Portfolio_/releases/tag/data-v1)

Assets esperados:

-   `olist_csv_raw.zip`: ZIP com os CSVs brutos da Olist.
-   `olist_colab.sqlite.zip`: opcional, ZIP com o banco `olist_colab.sqlite` pronto.

O notebook `01_preparacao_base_colab.ipynb` tenta baixar automaticamente:

``` text
https://github.com/Urpia-S/Portfolio_/releases/download/data-v1/olist_csv_raw.zip
```

Os notebooks `02` a `06` tentam baixar automaticamente o banco pronto, caso ele nao exista:

``` text
https://github.com/Urpia-S/Portfolio_/releases/download/data-v1/olist_colab.sqlite.zip
```

Com a Release `data-v1` publicada, os notebooks baixam os arquivos automaticamente.

## Estrutura

``` text
projeto SQL/
+-- notebooks/   versao principal do projeto em Google Colab
+-- docs/        explicacoes tecnicas e resumo de resultados
+-- outputs/     CSVs de resultados gerados
+-- sql/         versao alternativa em PostgreSQL
+-- data/        instrucao para organizar dados brutos localmente
```

## O que o projeto cobre

-   Carga dos CSVs locais.
-   Modelagem em camadas `stg_*`, `core_*` e `vw_*`.
-   Analise temporal de pedidos.
-   Receita, frete, estados e categorias.
-   Entregas, atrasos e satisfacao.
-   Segmentacao RFM.
-   Retencao e recompra.
-   Afinidade entre categorias.
-   Desempenho de vendedores.

## Versao PostgreSQL

A pasta `sql/` mantem uma versao reprodutivel em PostgreSQL, com scripts numerados. Ela e util para demonstrar modelagem relacional mais proxima de um ambiente de banco de dados real.

A versao principal para leitura e execucao no GitHub/Colab, entretanto, e a pasta `notebooks/`.
