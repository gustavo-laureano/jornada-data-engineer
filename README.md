# 🚀 Jornada Data Engineer

Este repositório contém o registro da minha evolução na trilha de Engenharia de Dados, utilizando a arquitetura **Lakehouse** com **Databricks** e **PySpark** guiada por [@nicolasn892](https://github.com/nicolasn892). O objetivo é simular cenários reais de ingestão, transformação e qualidade de dados.

## 🛠️ Tecnologias Utilizadas
* **Databricks** (Community Edition)
* **PySpark** (Spark SQL & DataFrames)
* **GitHub** para versionamento e portfólio

---

## 🎯 Missões Concluídas

### Missão 01: Iniciação no Lakehouse
* **Objetivo:** Configurar o ambiente de engenharia e rodar o primeiro pipeline de dados.
* **O que foi feito:**
    * Simulação da camada **Bronze** com dados manuais.
    * Transformação para a camada **Silver** com limpeza de nulos e lógica de aumento salarial (10%) para o departamento de TI.
    * Criação de uma regra de exceção: departamento "Gestão" não recebe aumento.
    * Agregação final (camada **Gold**) usando SQL para calcular média salarial por departamento.
* **Arquivo:** `Aula_01_Engenharia.ipynb`

### Missão 02: Integrar GitHub
* **Objetivo:** Integrar o Databricks ao GitHub para salvar e versionar o código.
* **O que foi feito:**
    * Configuração de **Personal Access Tokens (Classic)** no GitHub com permissão de `repo`.
    * Conexão via **Git Integration** nas configurações do Databricks.
    * Realização do primeiro *Commit & Push* do projeto diretamente do workspace.

### Missão 03: A Realidade dos Arquivos (Ingestão)
* **Objetivo:** Aprender a lidar com arquivos físicos (CSV) e sistema de arquivos DBFS.
* **O que foi feito:**
    * Upload de arquivo CSV externo para o **Data Lake** (DBFS) do Databricks.
    * Leitura dos dados usando `spark.read.format("csv")` com cabeçalho.
    * Adição de coluna `data_processamento` com o timestamp atual ajustado para o fuso horário local.
    * Escrita dos dados transformados em formato **Parquet** na pasta de saída `sales_silver`.
* **Arquivo:** `Aula_02_Ingestao.ipynb`

### Missão 04: O Pesadelo da Duplicidade (Quality)
* **Objetivo:** Resolver problemas de dados duplicados utilizando **Window Functions**.
* **O que foi feito:**
    * Criação de um DataFrame manual com IDs de venda repetidos e diferentes datas de atualização.
    * Implementação de uma janela (`Window`) particionada por `id_venda` e ordenada por `data_atualizacao` decrescente.
    * Uso da função `row_number()` para identificar a linha mais recente de cada venda.
    * Filtragem final para manter apenas os registros onde `rn == 1`.
* **Arquivo:** `Aula_03_WindowFunctions.ipynb`

---

## 🧠 Aprendizados Principais
* **Arquitetura Medallion:** Entendimento prático das camadas Bronze (dados brutos), Silver (limpeza e regras de negócio) e Gold (agregação para análise).
* **Qualidade de Dados:** Diferença fundamental entre usar `distinct()` (que remove linhas idênticas) e `row_number()` (que permite aplicar critérios lógicos para decidir qual registro é o "vencedor").
