
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 02 - Execucando comandos pelo Notebook

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é conhecer as funcionalidades de consulta (_Query_) da plataforma Databricks, utilizando a linguagem SQL (e as interfaces visuais), explorando os potenciais Analíticos. </br>





## Exercício 01.01 - Criação do database

``` sql
USE CATALOG academy;

CREATE DATABASE IF NOT EXISTS <seu_nome_login>;

USE <seu_nome_login>;
```

## Exercício 01.02 - Criação da Tabela

``` sql

CREATE OR REPLACE TABLE bronze_porte_empresa 
  ( porte_empresa      INT    COMMENT "codigo do porte da empresa",
    desc_porte_empresa STRING COMMENT "descricao do porte da empresa" )
COMMENT "Tabela auxiliar do porte das empresas"
```




