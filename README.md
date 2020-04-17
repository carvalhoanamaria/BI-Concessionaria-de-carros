[![author](https://img.shields.io/badge/author-AnaMariaCarvalho-red.svg)](https://www.linkedin.com/in/carvalhoanamaria/) [![](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html) [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/carvalhoanamaria) [![contributions welcome](https://img.shields.io/badge/redeSocial-lindedin-brightgreen.svg?style=flat)](https://www.linkedin.com/in/carvalhoanamaria)

# Utilizando Power BI, SSIS e SSAS para gerar insights em uma concessionária de veículos
<sub>*Meu primeiro projeto de Business Intelligence. (As informações aqui contidas são apenas ilustrativas para estudos.)*</sub>

<p align="center">
  <img src="img_con.png" >
</p>

## Análise das necessidades:
  O objetivo da aplicação dos metodos de BI nesse projeto são  para obter os seguintes conhecimentos:
* Desempenho do faturamento da corporação:
1. Qual o valor de faturamento e número de veículos vendidos por ano
(2015-2018) da corporação?

2. O faturamento das corporações estão acima ou abaixo da média?
* Desempenho do faturamento por veículo:
1. Quais modelos de veículos foram mais vendidos?
2. Como se encontra o comportamento de venda de cada fabricante?

* Perfil e preferência dos clientes:
1. Qual perfil predominante de cliente na escolha do veículo em cada
empresa?

## As ferramentas utilizadas:
* O SSIS: é uma plataforma que encontra se no pacote Business Intelligence Development Studio (BIDS) ou Visual Data Tools (SSDT) dependendo da versão do SQL Server utilizada, disponibilizada pela Microsoft, tem a finalidade de desenvolver processos de ETL.

* O SSAS é uma plataforma que também encontra se no pacote Business Intelligence Development Studio (BIDS) ou Visual Data Tools (SSDT) dependendo da versão do SQL Server utilizada, disponibilizada pela Microsoft, no qual permite o desenvolvimento de estruturas multidimensionais chamados cubo e modelo de mineração para a realização de análise de dados.

* SQL é uma linguagem de programação para modelos relacionais com a finalidade de manipulação, controle, transação e consultas de dados, desenvolvida pelo projeto System R nos laboratórios de IBM em San Jose.

## Modelagens do Data Warehouse:
   Nessa fase, o objetivo é definir o escopo para a criação do modelo do data warehouse logico e físico. O modelo escolhido para a modelagem do data warehouse foi o esquema estrela, composta por dimensões e fato, no qual tem como principal vantagem a fácil visualização dos dados e redução do número de Joins.
### Tabela dimensão:
* Dimensão Cliente: Dimensão onde é encontrado informações básicas do cliente. Tendo como chave primária código do cliente e atributos nome, idade e género do cliente.

* Dimensão Tempo: Dimensão onde é encontrada a chave primária controle e atributos data (dia/mês/ano) e ano em que cada dimensão é analisada.

* Dimensão Veiculo: Dimensão onde é encontrado as principais características do veículo. Tendo como chave primária código do veículo
e atributos modelo, cor, fabricante do veículo.

* Dimensão Loja: Dimensão onde é encontrado informações básicas da loja. Tendo como chave primária código da loja e atributos, cidade e
estado da loja.

### Tabela Fato: 
* Fato venda: Fato onde é encontrada a chave primária código venda e as chaves primárias das dimensões, código da venda, código do cliente, código da loja, código da data, código do veículo. Para as quais podem se navegar e analisar as informações desejadas. Este fato consiste também em a medida.

## Processo de ETL:

## Desenvolvimento dos Cubos:

## Desenvolvimento dos Dashboards:

## Resultados Obtidos:





