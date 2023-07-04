<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 04 - Criação de um ALERTA

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é explorar as funcionalidade de criação de um ALERTAl</br>
</br>

</br></br>

## Exercício 04.01 - Criação da Query

``` sql

select dolar_fechamento as valor_dolar
FROM academy.SEU_NOME.bronze_dolar
order by dolar_dia DESC;


```

## Exercício 04.02 - Criando o Alerta

Vamos utilizar a opção do menu  "**ALERT**".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab04_1.png" style="height: 200px;">


Clique no botão **CREATE** e configure o ALERTA conforme abaixo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab04_2.png" style="height: 500px;">


