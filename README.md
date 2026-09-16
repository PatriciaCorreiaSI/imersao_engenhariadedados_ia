# ✈️ Aviação ANAC → VoeBem Analytics

Materiais de estudo da turma da Imersão Engenharia de Dados — setembro/2026, com dados da ANAC, Python, SQL e Databricks.

A VoeBem Analytics é a consultoria fictícia usada no projeto: o objetivo é investigar atrasos, cancelamentos e pontualidade dos voos. Este repositório é uma iniciativa colaborativa da turma, sem vínculo oficial com a Alura.

O percurso é pelo navegador, com os dados incluídos e sem instalar Python ou Git no computador.

## Estrutura
- `dados/`: 15 CSVs da ANAC incluídos no material original: 12 meses de VRA (agosto/2025 a julho/2026) e três cadastros de referência.
- `notebooks/`: ingestão Bronze, transformação Silver e governança Gold. Os arquivos .py estão no formato de notebooks Databricks.


## Preparação

A instalação local é necessária somente se você optar pelos scripts de terminal. Use Python 3.10 ou superior para esses scripts. 
Eles utilizam a biblioteca padrão. Os notebooks dependem do ambiente Spark/Databricks e não devem ser executados como scripts Python locais.

- Baixe ou clone este repositório e abra um terminal na pasta do projeto.
- Execute python scripts/baixar_anac.py para baixar os CSVs e copie-os para a pasta `dados/`.
  Para recuperar arquivos ausentes, execute `python scripts/baixar_anac.py`.
  O script usa a janela agosto/2025 a julho/2026, reaproveita arquivos existentes e atualiza `docs/fontes.md` com o registro do download.
  A disponibilidade de novos downloads depende do portal de origem.
- Crie uma conta no [Databricks](https://login.databricks.com)
- Abra seu ambiente de estudos no Databricks, execute `sql/00_preparar_ambiente.sql`. É necessário ter permissão para criar catálogo, schemas e volume.
- Envie o conteúdo de `dados/vra/` para `/Volumes/voebem/bronze/arquivos/vra/` e o conteúdo de `dados/referencias`/ para `/Volumes/voebem/bronze/arquivos/referencias/`.
- Importe os arquivos de `notebooks`/ como notebooks Databricks.

O código usa o catálogo `voebem`. Se escolher outro nome, ajuste as referências nos notebooks, SQL e configuração do Genie. As cargas usam sobrescrita ou `CREATE OR REPLACE`: execute no ambiente destinado a este projeto.

## Sequência de estudos e execução
1. `notebooks/bronze_vra.py`
2. `notebooks/bronze_referencias.py`
3. `notebooks/silver_espelho.py`

## Créditos

Contexto educacional: Imersão Engenharia de Dados da Alura, setembro/2026. Fonte dos dados: ANAC, conforme docs/fontes.md. O código-base foi preservado a partir do material compartilhado da imersão, com ajustes de preparação para publicação.
