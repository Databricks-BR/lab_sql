
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 01 - Explorando o Editor de Query

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é conhecer as funcionalidades de consulta (_Query_) da plataforma Databricks, utilizando a linguagem SQL (e as interfaces visuais), explorando os potenciais Analíticos. </br>
</br>
Os exercícios deverão ser executados na opção do Menu lateral "**SQL Editor**".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab01_editor_sql.png">


</br></br></br>
## Sessão 01:  Estrutura TABELAS, DATABASE e CATÁLOGOS

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab01_uc.png">


| Tópico | Comando |
| -- | -- |
| **Catálogo** | CREATE CATALOG <nome_catalogo> |
| **Schema** | CREATE DATABASE IF NOT EXISTS <nome_catalogo>.<nome_database>; |
| **Tabela** | CREATE OR REPLACE TABLE  <nome_catalogo>.<nome_database>.<nome_tabela>; |
| **View** |  CREATE OR REPLACE VIEW  <nome_catalogo>.<nome_database>.<nome_tabela> AS ...; |

#### Referência:
* [Databricks Help - DDL Syntax](https://docs.databricks.com/sql/language-manual/sql-ref-syntax-ddl-create-table.html)

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

 ## Exercício 01.03 - Inserindo dados na Tabela através de SQL INSERT

 ``` sql
 INSERT INTO bronze_porte_empresa VALUES (1, "NAO INFORMADO") ;
 INSERT INTO bronze_porte_empresa VALUES (2, "MICRO EMPRESA") ;
 INSERT INTO bronze_porte_empresa VALUES (3, "PEQUENO PORTE") ;
 INSERT INTO bronze_porte_empresa VALUES (4, "NAO SEI") ;
 INSERT INTO bronze_porte_empresa VALUES (5, "NULL") ;
```

 ## Exercício 01.04 - Verificando o conteúdo da TABELA

 ``` sql
SELECT * 
FROM bronze_porte_empresa 
ORDER BY porte_empresa
```

 ## Exercício 01.05 - Alterando o conteúdo da TABELA

 ``` sql
UPDATE bronze_porte_empresa  
SET desc_porte_empresa = "OUTROS" 
WHERE porte_empresa = 5;


DELETE 
FROM bronze_porte_empresa 
WHERE porte_empresa = 4;
```

## Exercício 01.06 - Visualizando o Histórico de Atualizações da tabela

 ``` sql
DESCRIBE HISTORY bronze_porte_empresa 
```

## Exercício 01.07 - Visualizando o conteúdo da tabela na versão anterior (TIME TRAVEL)

 ``` sql
SELECT * FROM bronze_porte_empresa VERSION AS OF 5
```

## Exercício 01.08 - RESTAURANDO o conteúdo da tabela na versão anterior (TIME TRAVEL)

 ``` sql
RESTORE TABLE bronze_porte_empresa TO VERSION AS OF 5 
```

## Exercício 01.09 - Visualizando as propriedades da Tabela

 ``` sql
DESCRIBE DETAIL bronze_porte_empresa 
```

## Exercício 01.10 - Visualizando as informações DETALHADAS da Tabela

 ``` sql
DESCRIBE TABLE EXTENDED bronze_porte_empresa
```
