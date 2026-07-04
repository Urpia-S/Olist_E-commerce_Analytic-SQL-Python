# Notebooks Colab

Versao principal do projeto, pensada para ser aberta a partir do GitHub e executada no Google Colab.

## Ordem recomendada

| Ordem | Notebook | Conteudo |
|--------------------:|------------------|------------------|
| 1 | `01_preparacao_base_colab.ipynb` | Upload/download dos CSVs, carga em SQLite, staging, core e views. |
| 2 | `02_temporal_receita_colab.ipynb` | Pedidos por tempo, receita, frete, estados e categorias. |
| 3 | `03_entregas_satisfacao_colab.ipynb` | Prazos, atrasos, reviews e impacto da entrega na satisfacao. |
| 4 | `04_rfm_retencao_colab.ipynb` | Segmentacao RFM, recompra e coortes de retencao. |
| 5 | `05_afinidade_vendedores_colab.ipynb` | Categorias compradas juntas, vendedores e resumo executivo. |
| 6 | `06_playground_consultas_sql_colab.ipynb` | Area livre para testar novas consultas SQL. |

## Dados

O notebook `01` tenta baixar automaticamente os CSVs de:

``` text
https://github.com/Urpia-S/Portfolio_/releases/download/data-v1/olist_csv_raw.zip
```

Os notebooks `02` a `06` tentam baixar automaticamente o banco pronto de:

``` text
https://github.com/Urpia-S/Portfolio_/releases/download/data-v1/olist_colab.sqlite.zip
```

Com esses assets publicados na Release `data-v1`, os notebooks baixam os arquivos automaticamente.
