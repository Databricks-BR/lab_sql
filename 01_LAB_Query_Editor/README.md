
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 01 - Explorando o Editor de Query

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é conhecer as funcionalidades de consulta (_Query_) da plataforma Databricks, utilizando a linguagem SQL (e as interfaces visuais), explorando os potenciais Analíticos. </br>
</br>

## Sessão:  Estrutura TABELAS, DATABASE e CATÁLOGOS

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab01_uc.png">

| -- | -- |
| Tópico | Comando |
| -- | -- |
| **Catálogo** | CREATE CATALOG <nome_catalogo> |
| **Schema** | CREATE DATABASE IF NOT EXISTS <nome_catalogo>.<nome_database>; |
| **Tabela** | CREATE TABLE IF NOT EXISTS <nome_catalogo>.<nome_database>.<nome_tabela>; |
| -- | -- |

## Exercício 01.01 - Criação do database

``` sql

USE CATALOG academy;

CREATE DATABASE IF NOT EXISTS <seu_nome_login>;

GRANT ALL PRIVILEGES ON DATABASE <seu_nome>_dbacademy TO `learner’s_username`;

USE <seu_nome>_dbacademy;


CREATE TABLE intro_to_databricks_sql_gym_logs
USING JSON
LOCATION ‘wasbs://courseware@dbacademy.blob.core.windows.net/introduction-to-databricks-sql/v01/gym-logs’;

```

## Exercício 01 - Criação do database

``` sql

CREATE DATABASE IF NOT EXISTS <seu_nome>_dbacademy;


GRANT ALL PRIVILEGES ON DATABASE <seu_nome>_dbacademy TO `learner’s_username`;

USE <seu_nome>_dbacademy;


CREATE TABLE intro_to_databricks_sql_gym_logs
USING JSON
LOCATION ‘wasbs://courseware@dbacademy.blob.core.windows.net/introduction-to-databricks-sql/v01/gym-logs’;

```

## Exercício 02 - SQL de visualização simples

``` sql
SELECT
 *
FROM
 <seu_nome>_dbacademy.intro_to_databricks_sql_gym_logs;
``` 

 ## Exercício 03 - Verificando as Academias mais Populares
 
``` sql
SELECT
 gym,
 count(gym)
FROM
 <seu_nome>_dbacademy.intro_to_databricks_sql_gym_logs
GROUP BY
 gym
ORDER BY
 gym;
``` 
## Exercício 04 - Avaliando a faixa (range) de Datas 

``` sql

SELECT
 from_unixtime(min(first_timestamp), “d MMMM y”) First_Date,
 from_unixtime(max(last_timestamp), “d MMMM y”) Last_Date
FROM
 <seu_nome>_dbacademy.intro_to_databricks_sql_gym_logs;
``` 

## Exercício 05 - Calculando a média de tempo na academia

``` sql

SELECT
 from_unixtime(first_timestamp, “dd”) as day,
 avg((last_timestamp - first_timestamp) / 60) as avg_time
FROM
 <seu_nome>_dbacademy.intro_to_databricks_sql_gym_logs
group by
 day
ORDER BY
 from_unixtime(first_timestamp, “dd”); (edited) 
```  
