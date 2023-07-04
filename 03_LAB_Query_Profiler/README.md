
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 03 - Explorando o Query Profiler 

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é explorar as funcionalidade de plano de execução das consultas (Query Profiler). Sabendo identificar os gargalos e oportunidades de melhoria de desempenho. </br>
</br>


<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/desnormaliza.png">

Vamos utilizar o "Editor SQL".

## Exercício 03.01 - Criação da Query

``` sql
USE CATALOG academy;

USE <seu_nome_login>;

CREATE OR REPLACE TABLE silver_empresas AS
SELECT 
  est.cnpj_basico AS cnpj_basico,
  matriz_filial AS nome_matriz,
  nome_fantasia AS nome_fantasia_empresa,
  razao_social AS nome_razao_social,
  codigo_situacao_cadastral AS cod_situacao_cadastral,
  data_situacao_cadastral AS data_situacao_cadastral,
  motivo_situacao_cadastral AS motivo_situacao_cadastral,
  data_inicio_atividade AS data_inicio_atividade,
  cnae_principal AS cnae_principal,
  cnae.descricao AS cnae_descricao,
  tipo_logradouro AS endereco_tipo_logradouro,
  logradouro AS endereco_nome_logradouro,
  numero AS endereco_numero_logradouro,
  bairro AS endereco_bairro_logradouro,
  cep AS endereco_numero_cep,
  uf AS endereco_unidade_federativa,
  codigo_municipio_siafi AS codigo_municipio_siafi,
  natureza_juridica AS cod_natureza_juridica,
  nat.descricao AS desc_natureza_juridica,
  qualificacao_responsavel AS qualificacao_responsavel,
  capital_social AS val_capital_social,
  emp.porte_empresa AS cod_porte_empresa,
  porte.desc_porte_empresa AS desc_porte_empresa,
  ente_federativo_responsavel AS ente_federativo_responsavel
from bronze_estabelecimentos est
join bronze_empresas emp
on est.cnpj_basico = emp.cnpj_basico
left join bronze_cnae cnae
on est.cnae_principal = cnae.cod_cnae
left join bronze_porte_empresa porte
on emp.porte_empresa = porte.porte_empresa
left join bronze_naturezas nat
on emp.natureza_juridica = nat.codigo;


```

## Exercício 03.02 - Visualizando o Histórico de execução das Consultas


No Menu, escolha a opção "Query History"

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_1.png" style="height: 200px;">

Filtre as Consultas (p.ex.  Selecione suas próprias Queries):

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_2.png" style="height: 300px;">

## Exercício 03.03 - Analisando o Detalhe da Execução

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_3.png" style="height: 200px;">


## Exercício 03.04 - Analisando o Query Profiler

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_4.png" style="height: 200px;">


## Exercício 03.05 - Analisando o Plano de Execução

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_5.png" style="height: 250px;">

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab03_6.png" style="height: 700px;">


## Exercício 03.06 - Colocando Comentários na Tabela e nas Colunas

``` sql
USE CATALOG academy;

USE <seu_nome_login>;

COMMENT ON TABLE silver_empresas IS 'Tabela contendo dados das empresas';

ALTER TABLE silver_empresas ALTER COLUMN cnpj_basico COMMENT 'número do CNPJ raiz de 8 posições';
ALTER TABLE silver_empresas ALTER COLUMN nome_matriz COMMENT 'Nome da Matriz';
ALTER TABLE silver_empresas ALTER COLUMN nome_fantasia_empresa COMMENT 'Nome fantasia da empresa';
ALTER TABLE silver_empresas ALTER COLUMN nome_razao_social COMMENT 'Nome da Razão Social';
ALTER TABLE silver_empresas ALTER COLUMN cod_situacao_cadastral COMMENT 'Código da Situação Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN data_situacao_cadastral COMMENT 'Data da Situação Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN motivo_situacao_cadastral COMMENT 'Motivo da Situação Cadastral';
ALTER TABLE silver_empresas ALTER COLUMN data_inicio_atividade COMMENT 'Data de início da atividade';
ALTER TABLE silver_empresas ALTER COLUMN cnae_principal COMMENT 'CNAE Código da Natureza Economica';
ALTER TABLE silver_empresas ALTER COLUMN cnae_descricao COMMENT 'Descrição do CNAE';
ALTER TABLE silver_empresas ALTER COLUMN endereco_tipo_logradouro COMMENT 'Endereço - Tipo de Logradouro';
ALTER TABLE silver_empresas ALTER COLUMN endereco_nome_logradouro COMMENT 'Endereço - Nome do Logradouro';
ALTER TABLE silver_empresas ALTER COLUMN endereco_numero_logradouro COMMENT 'Endereço - Número do Logradouro';
ALTER TABLE silver_empresas ALTER COLUMN endereco_bairro_logradouro COMMENT 'Endereço - Bairro do Logradouro';
ALTER TABLE silver_empresas ALTER COLUMN endereco_numero_cep COMMENT 'Endereço - número do CEP';
ALTER TABLE silver_empresas ALTER COLUMN endereco_unidade_federativa COMMENT 'Endereço - Unidade Federativa';
ALTER TABLE silver_empresas ALTER COLUMN codigo_municipio_siafi COMMENT 'Código do Município SIAFI';
ALTER TABLE silver_empresas ALTER COLUMN cod_natureza_juridica COMMENT 'Código da Natureza Jurídica';
ALTER TABLE silver_empresas ALTER COLUMN desc_natureza_juridica COMMENT 'Descrição da Natureza Jurídica';
ALTER TABLE silver_empresas ALTER COLUMN qualificacao_responsavel COMMENT 'Qualificação do Responsável';
ALTER TABLE silver_empresas ALTER COLUMN val_capital_social COMMENT 'Valor do Capital Social';
ALTER TABLE silver_empresas ALTER COLUMN cod_porte_empresa COMMENT 'Código do Porte da Empresa';
ALTER TABLE silver_empresas ALTER COLUMN desc_porte_empresa COMMENT 'Descrição do Porte da Empresa';
ALTER TABLE silver_empresas ALTER COLUMN ente_federativo_responsavel COMMENT 'Ente Federativo Responsável';
```

