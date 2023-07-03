
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


select est.*, 
       razao_social,natureza_juridica,qualificacao_responsavel,capital_social,porte_empresa,ente_federativo_responsavel,
       cnae.descricao cnae_descricao
from bronze_estabelecimentos est
join bronze_empresas emp
on est.cnpj_basico = emp.cnpj_basico
left join bronze_cnae cnae
on est.cnae_principal = cnae.cod_cnae;


```

## Exercício 03.02 - Analisando o Query Profiler



