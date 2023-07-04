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
</br></br>

## Exercício 05.02 - Criando a Visualização e o Filtro

Na barra de resultados, clique no botão **"+"**, e escolha a opção "Visualization".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_02.png" style="height: 200px;">

</br></br>
No Visualization Type, escolha "LINE":

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_03.png" style="height: 200px;">

</br></br>
Na "X Column" (eixo X), escolha a variável  "dolar_dia".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_04.png" style="height: 200px;">

</br></br>
Na "Y Columns" (eixo Y), escolha a variável  "dolar_fechamento".</br>
Escolha também a forma de agregação:  Média (Average).

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_05.png" style="height: 200px;">

</br></br>
Clique no título da visualização e renomeie para "grafico_dolar".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_06.png" style="height: 150px;">

O resultado esperado é igual ao gráfico abaixo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_07.png" style="height: 500px;">

</br></br>

Clique novamente no botão **"+"**, e adicione um FILTRO:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_09.png" style="height: 150px;">

</br></br>

Escolha a coluna "dolar_ano" para utilizar no FILTRO:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_10.png" style="height: 300px;">

</br></br>
Resultado ficará como abaixo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_11.png" style="height: 250px;">

</br></br>

Salve o resultado da Query, com o nome:   "Query_Historico_dolar_" +  <SEU_NOME>.
</br></br></br>

## Exercício 05.03 - Criando o Dashboard

No Menu Lateral, escolha a opção DASHBOARDS:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_08.png" style="height: 150px;">
</br></br>

Clique na opção **CREATE DASHBOARD**

</br></br>
</br></br>

Na tela do Dashboard, clique no botão **"ADD"**, e escolha a opção:  "**TEXT BOX**".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_12.png" style="height: 100px;">

No campo texto, digite conforme abaixo:

``` md

![alt text](https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_handson_sql.png)


```

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_13.png" style="height: 300px;">

Repita a operação.  Clique no botão **ADD**, e novamente a opção "Text Box".  Digite conforme abaixo:

``` md


![alt text](https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/header_dolar.png)

```

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_14.png" style="height: 200px;">

Clique novamente no botão ADD, e selecione a opção "**VISUALIZATION**".

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_15.png" style="height: 200px;">

Escolha o nome da Query que foi gravada no exercício anterior.

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_16.png" style="height: 250px;">

Clique novamente no botão ADD, e selecione a opção "**FILTER**", e configure conforme abaixo:

<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_17.png" style="height: 200px;">

</br></br></br>

O Resultado final deve ficar conforme abaixo.   Grave seu Dashboard.

</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/lab_sql/main/images/lab05_final.png" style="height: 600px;">
