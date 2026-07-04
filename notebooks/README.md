# Notebooks Colab

Versao principal do projeto, pensada para ser aberta a partir do GitHub e executada no Google Colab.

## Ordem recomendada

| Ordem | Notebook | Conteudo | Abrir no Colab |
|------:|----------|----------|----------------|
| 1 | `01_preparacao_base_colab.ipynb` | Upload/download dos CSVs, carga em SQLite, staging, core e views. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/01_preparacao_base_colab.ipynb) |
| 2 | `02_temporal_receita_colab.ipynb` | Pedidos por tempo, receita, frete, estados e categorias. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/02_temporal_receita_colab.ipynb) |
| 3 | `03_entregas_satisfacao_colab.ipynb` | Prazos, atrasos, reviews e impacto da entrega na satisfacao. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/03_entregas_satisfacao_colab.ipynb) |
| 4 | `04_rfm_retencao_colab.ipynb` | Segmentacao RFM, recompra e coortes de retencao. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/04_rfm_retencao_colab.ipynb) |
| 5 | `05_afinidade_vendedores_colab.ipynb` | Categorias compradas juntas, vendedores e resumo executivo. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/05_afinidade_vendedores_colab.ipynb) |
| 6 | `06_playground_consultas_sql_colab.ipynb` | Area livre para testar novas consultas SQL. | [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/blob/main/notebooks/06_playground_consultas_sql_colab.ipynb) |

## Dados

O notebook `01` tenta baixar automaticamente os CSVs de:

``` text
https://github.com/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/releases/download/data-v1/olist_csv_raw.zip
```

Os notebooks `02` a `06` tentam baixar automaticamente o banco pronto de:

``` text
https://github.com/Urpia-S/Olist_E-commerce_Analytic-SQL-Python/releases/download/data-v1/olist_colab.sqlite.zip
```

Com esses assets publicados na Release `data-v1`, os notebooks baixam os arquivos automaticamente.

As consultas que exportam resultados salvam novos CSVs em `outputs_colab/` durante a execucao no Colab.
