<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png">

# Hands-On LAB 05 - Explorando o Dashboard (Painel Gerencial)

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Analytics (SQL, Query, Dask, DataViz, SQL end-point).


## Objetivos do Exercício

O objetivo desse laboratório é explorar as funcionalidade de consultas com Gráficos de Visualização e Filtros para depois montar um Painel Gerencial</br>
</br>

Vamos utilizar o "Editor SQL".

## Exercício 05.01 - Criação da Query

``` sql

SELECT * FROM academy.SEU_NOME.bronze_dolar;

```
Resultado da Query:
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_01.png" style="height: 200px;">

## Exercício 05.02 - Criando a Visualização e o Filtro

Na barra de resultados, clique no botão **"+"**, e escolha a opção "Visualization".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_02.png" style="height: 200px;">

No Visualization Type, escolha "LINE":

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_03.png" style="height: 200px;">

Na "X Column" (eixo X), escolha a variável  "dolar_dia".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_04.png" style="height: 200px;">

Na "Y Columns" (eixo Y), escolha a variável  "dolar_fechamento".</br>
Escolha também a forma de agregação:  Média (Average).

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_05.png" style="height: 200px;">

Clique no título da visualização e renomeie para "grafico_dolar".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_06.png" style="height: 200px;">

O resultado esperado é igual ao gráfico abaixo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_07.png" style="height: 200px;">

## Exercício 05.03 - Criando o Dashboard

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_08.png" style="height: 200px;">

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_09.png" style="height: 200px;">

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_10.png" style="height: 200px;">
