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

Para que os notebooks funcionem para qualquer pessoa que abrir pelo GitHub, a Release `data-v1` deste repositorio concentra os arquivos de dados:

[Release data-v1](https://github.com/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/releases/tag/data-v1)

Assets esperados:

-   `olist_csv_raw.zip`: ZIP com os CSVs brutos da Olist.
-   `olist_colab.sqlite.zip`: opcional, ZIP com o banco `olist_colab.sqlite` pronto.

O notebook `01_preparacao_base_colab.ipynb` tenta baixar automaticamente:

``` text
https://github.com/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/releases/download/data-v1/olist_csv_raw.zip
```

Os notebooks `02` a `06` tentam baixar automaticamente o banco pronto, caso ele nao exista:

``` text
https://github.com/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/releases/download/data-v1/olist_colab.sqlite.zip
```

Com a Release `data-v1` publicada, os notebooks baixam os arquivos automaticamente.

## Estrutura

``` text
Olist_E-commerce_Analytic-SQL-Python/
+-- notebooks/   versao principal do projeto em Google Colab
+-- docs/        explicacoes tecnicas e resumo de resultados
+-- outputs/     CSVs de resultados versionados
```

Ao executar os notebooks no Colab, os novos CSVs sao gravados em `outputs_colab/`.

## O que o projeto cobre

-   Download e carga dos CSVs da Olist.
-   Modelagem em camadas `stg_*`, `core_*` e `vw_*`.
-   Analise temporal de pedidos.
-   Receita, frete, estados e categorias.
-   Entregas, atrasos e satisfacao.
-   Segmentacao RFM.
-   Retencao e recompra.
-   Afinidade entre categorias.
-   Desempenho de vendedores.
