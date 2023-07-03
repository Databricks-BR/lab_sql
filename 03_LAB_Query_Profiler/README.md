
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

create or replace table silver_empresas as
select est.cnpj_basico                   COMMENT "número do CNPJ raiz de 8 posições",
       matriz_filial                     COMMENT "Nome da Matriz",
       nome_fantasia                     COMMENT "Nome fantasia da empresa",
       razao_social                      COMMENT "Nome da Razão Social",
       codigo_situacao_cadastral         COMMENT "Código da Situação Cadastral",
       data_situacao_cadastral           COMMENT "Data da Situação Cadastral",
       motivo_situacao_cadastral         COMMENT "Motivo da Situação Cadastral",
       data_inicio_atividade             COMMENT "Data de início da atividade",
       cnae_principal                    COMMENT "CNAE Código da Natureza Economica",
       cnae.descricao cnae_descricao     COMMENT "Descrição do CNAE",
       tipo_logradouro                   COMMENT "Endereço - Tipo de Logradouro",
       logradouro                        COMMENT "Endereço - Nome do Logradouro",
       numero                            COMMENT "Endereço - Número do Logradouro",
       bairro                            COMMENT "Endereço - Bairro do Logradouro",
       cep                               COMMENT "Endereço - número do CEP",
       uf                                COMMENT "Endereço - Unidade Federativa",
       codigo_municipio_siafi            COMMENT "Código do Município SIAFI",
       natureza_juridica                 COMMENT "Código da Natureza Jurídica",
       nat.descricao natureza_descricao  COMMENT "Descrição da Natureza Jurídica"
       qualificacao_responsavel          COMMENT "Qualificação do Responsável",
       capital_social                    COMMENT "Valor do Capital Social",
       emp.porte_empresa                 COMMENT "Código do Porte da Empresa",
       porte.desc_porte_empresa          COMMENT "Descrição do Porte da Empresa",
       ente_federativo_responsavel       COMMENT "Ente Federativo Responsável"       
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



