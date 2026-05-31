# 📊 Miniprojeto — Análise Exploratória de Dados (Varejo)

## 📌 Descrição do Projeto

O presente projeto consiste em uma Análise Exploratória de Dados (AED) aplicada a uma base de dados do setor varejista, desenvolvida em Python com o suporte das bibliotecas Pandas, NumPy, Matplotlib e Jupyter Notebook.

O objetivo é compreender, limpar e estruturar os dados, além de extrair estatísticas descritivas e identificar padrões relevantes de comportamento dos clientes. O projeto possui caráter educacional, visando o desenvolvimento de habilidades em preparação de dados e análise exploratória.

## 🔄 ETL e Qualidade de Dados

O projeto segue os princípios do processo de ETL (Extract, Transform, Load):

Extract (Extração): importação da base de dados em formato CSV.
Transform (Transformação): tratamento de valores nulos, remoção de colunas sem relevância, padronização de categorias, conversão de tipos de dados e remoção de duplicidades.
Load (Carga): utilização da base tratada para análises exploratórias e geração de insights.

Essas etapas garantem a qualidade dos dados, assegurando consistência, integridade e confiabilidade das análises realizadas.

## 📥 Leitura e Estruturação dos Dados

A base Base Varejo.csv foi carregada utilizando Pandas.
Foi necessário definir o separador ;, pois o arquivo não seguia o padrão de vírgula.

Essa etapa foi essencial para garantir a correta estruturação dos dados em formato tabular.

## 🧹 Tratamento e Limpeza dos Dados

Foram realizadas as seguintes etapas de preparação:

Identificação de valores nulos com isnull()
Remoção de colunas vazias (Unnamed)
Conversão da coluna DATA para formato datetime
Substituição de valores inconsistentes (#N/D → sem Categoria)
Remoção de registros duplicados

Essas ações são fundamentais para garantir a qualidade e confiabilidade da base de dados.

## 🔁 Transformação dos Dados

Foram aplicadas transformações para adequação da análise:

Mapeamento de variáveis categóricas
Padronização de informações inconsistentes
Estruturação dos dados para análises agregadas

Essas transformações permitem uma melhor interpretação dos dados e facilitam análises estatísticas.

## 📊 Agrupamento 1 — Gênero x Segmento

Este agrupamento analisa a quantidade de clientes por gênero (CL_GENERO) e segmento (CL_SEG).


```python
genero_segmento = (
    df.groupby(['CL_GENERO', 'CL_SEG'])
      .size()
      .reset_index(name='Quantidade')
)

grafico = genero_segmento.pivot(
    index='CL_SEG',
    columns='CL_GENERO',
    values='Quantidade'
)
```

Esse agrupamento permite visualizar a distribuição de clientes entre diferentes perfis.

## 📊 Agrupamento 2 — Categoria x Gênero x Estado Civil

Este agrupamento analisa a quantidade de compras por categoria de produto (PR_CAT), considerando também gênero e estado civil.

```python
df['CL_EC_DESC'] = df['CL_EC'].map(estado_civil)

agrupamento = (
    df.groupby(['PR_CAT', 'CL_GENERO', 'CL_EC_DESC'])
      .size()
      .reset_index(name='Quantidade')
)

pivot = agrupamento.pivot_table(
    index='PR_CAT',
    columns=['CL_GENERO', 'CL_EC_DESC'],
    values='Quantidade',
    fill_value=0
)
```
Esse agrupamento permite identificar padrões de consumo mais detalhados entre diferentes perfis de clientes.

## 📈 Importância da Visualização

Os gráficos gerados com Matplotlib permitem transformar dados numéricos em informações visuais, facilitando a identificação de padrões, tendências e comparações entre grupos.

## 📌 Insights Obtidos
Há variação significativa na distribuição de clientes entre segmentos.
O gênero influencia a distribuição dos clientes por segmento.
O estado civil impacta padrões de consumo em diferentes categorias.
Categorias de produtos apresentam variações relevantes quando cruzadas com variáveis demográficas.
A qualidade dos dados impacta diretamente a confiabilidade das análises.
O processo de limpeza foi essencial para garantir consistência nos resultados.


## 🚀 Conclusão

O projeto permitiu aplicar conceitos fundamentais de análise de dados, incluindo:

ETL (Extração, Transformação e Carga)
Limpeza e tratamento de dados
Conversão de tipos e padronização
Agrupamentos com groupby e/ou pivot_table
Visualização de dados com gráficos

Conclui-se que a análise exploratória é uma etapa essencial para compreender a estrutura dos dados e gerar insights relevantes para tomadas de decisão.

## ⚙️ Tecnologias Utilizadas
Python

Pandas

NumPy

Matplotlib

Nbstripout

Jupyter Notebook

Git / GitHub

venv

requirements.txt

.gitignore


