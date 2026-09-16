# ✈️ Aviação ANAC → VoeBem Analytics

Materiais de estudo da turma da Imersão Engenharia de Dados — setembro/2026, com dados da ANAC, Python, SQL e Databricks.

A VoeBem Analytics é a consultoria fictícia usada no projeto: o objetivo é investigar atrasos, cancelamentos e pontualidade dos voos. Este repositório é uma iniciativa colaborativa da turma, sem vínculo oficial com a Alura.

O percurso é pelo navegador, com os dados incluídos e sem instalar Python ou Git no computador.

## Estrutura
- `dados/`: 15 CSVs da ANAC incluídos no material original: 12 meses de VRA (agosto/2025 a julho/2026) e três cadastros de referência.
- `notebooks/`: ingestão Bronze, transformação Silver e governança Gold. Os arquivos .py estão no formato de notebooks Databricks.
- `sql`: arquivo de preparação do ambiente no Databricks.
- `scripts/`: download dos dados e utilitários opcionais de execução e Genie.
- `docs/`: fontes, 


## Preparação

A instalação local é necessária somente se você optar pelos scripts de terminal. Use Python 3.10 ou superior para esses scripts. 
Eles utilizam a biblioteca padrão. Os notebooks dependem do ambiente Spark/Databricks e não devem ser executados como scripts Python locais.

- Baixe ou clone este repositório e abra um terminal na pasta do projeto.
- Os CSVs já estão incluídos em `dados/`, portanto não é necessário baixá-los novamente.
Para recuperar arquivos ausentes, execute `python scripts/baixar_anac.py`.
O script usa a janela agosto/2025 a julho/2026, reaproveita arquivos existentes e atualiza `docs/fontes.md` com o registro do download.
A disponibilidade de novos downloads depende do portal de origem.
- Crie uma conta no [Databricks](https://login.databricks.com)
- Abra seu ambiente de estudos no Databricks, execute `sql/00_preparar_ambiente.sql`. É necessário ter permissão para criar catálogo, schemas e volume.
- Envie o conteúdo de `dados/vra/` para `/Volumes/voebem/bronze/arquivos/vra/` e o conteúdo de `dados/referencias`/ para `/Volumes/voebem/bronze/arquivos/referencias/`.
- Importe os arquivos de `notebooks`/ como notebooks Databricks.

O código usa o catálogo `voebem`. Se escolher outro nome, ajuste as referências nos notebooks, SQL e configuração do Genie. As cargas usam sobrescrita ou `CREATE OR REPLACE`: execute no ambiente destinado a este projeto.

## Sequência de estudos e execução

### ✅Concluído:

1. `notebooks/bronze_vra.py`
2. `notebooks/bronze_referencias.py`
3. `notebooks/silver_espelho.py`

### 🏗️ Em construção:

4. Configure um pipeline de qualidade com os três arquivos de pipelines/qualidade/, catálogo voebem e schema silver, e execute-o no Databricks. Para usar sql/metricas_qualidade.sql, configure também a publicação do event log do pipeline na tabela voebem.silver.eventos_qualidade.
5. Execute sql/gold/01_dim_aeroporto.sql, 02_fato_voos.sql e 03_obt_voos.sql, nessa ordem.
6. Execute notebooks/09_governanca_gold.py.
7. Explore as consultas em sql/gabarito/ e as perguntas em docs/perguntas-de-negocio.md.
8. Opcional: configure um espaço Genie com voebem.gold.obt_voos, usando os exemplos e instruções de genie/. O script python scripts/montar_genie_space.py regenera o JSON; ele não cria o espaço no serviço.

## Créditos

Contexto educacional: Imersão Engenharia de Dados da Alura, setembro/2026. Fonte dos dados: ANAC, conforme docs/fontes.md. O código-base foi preservado a partir do material compartilhado da imersão, com ajustes de preparação para publicação.
