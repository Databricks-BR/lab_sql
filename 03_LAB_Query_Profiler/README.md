
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

## Exercício 03.02 - Analisando o Query Profiler



