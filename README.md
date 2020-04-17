[![author](https://img.shields.io/badge/author-AnaMariaCarvalho-red.svg)](https://www.linkedin.com/in/carvalhoanamaria/) [![](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html) [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/carvalhoanamaria) [![contributions welcome](https://img.shields.io/badge/redeSocial-lindedin-brightgreen.svg?style=flat)](https://www.linkedin.com/in/carvalhoanamaria)

# Utilizando Power BI, SSIS e SSAS para gerar insights em uma concessionária de veículos
<sub>*Meu primeiro projeto de Business Intelligence. (As informações aqui contidas são apenas ilustrativas para estudos.)*</sub>

<p align="center">
  <img src="img_todos.png" >
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

#### Modelo Lógico  do data Warehouse
<p align="center">
  <img src="Data-warehouse/Modelo Logico do data warehouse.jpg" width="550" height="500" >
</p>
#### Modelo Físico do data Warehouse
<sub>* Data-warehouseModelo/ Modelo Fisico Create do data warehouse.sql*</sub>

## Processo de ETL:
Para a criação do ETL foi dividido o processo em pacotes, contendo em cada pacote uma tabela para um melhor entendimento. Assim, para
cada tabela é criado um mapeamento especificando de onde as informações estão sendo obtidas e para onde serão carregadas.

<sub>*BI-Concessionaria-de-carros/Processos de ETL/*</sub>

 * As respectivas tabelas DIM_LOJA, DIM_CLIENTE, DIM_VEICULO foi utilizada em seu fluxo de dados o componente Excel Source, correspondente a fonte de origem, seguido pela transformação Data Conversion, responsável por converter os tipos de dados das colunas de entrada em uma nova coluna de acordo com o padrão dos dados de saída, para não haver nenhuma incompatibilidade no momento do armazenamento. Por sua vez, a transformação Sort foi encarregada de ordenar os dados de entrada de modo crescente e remover as linhas duplicadas. Por fim, foi aplicado o componente OLE DB Destination, no qual foi vinculado ao data warehouse criado e mapeado com os dados aqui tratados para a carga do mesmo.
 
 * A tabela DIM_TEMPO no fluxo de dados foi usada também o componente Excel Source e a transformação Data Conversion. Contudo, após foi aplicado a transformação aggregate, com a finalidade de agrupar os registros em dois grupos, um grupo contendo data de saída do veículo e outro grupo contendo ano de saída do veículo, possibilitando a combinação de dados ano e data, pois para cada ano de saída, possui várias datas de saída de veículos. Em seguida, foi utilizado a transformação Sort e por fim, foi aplicado o componente OLE DB Destination que vincula ao data warehouse para o armazenamento dos dados.
 
 * A tabela FATO_VENDA, no fluxo de dados foi utilizado o componente Excel Source e a transformação Data Conversion, seguido pela transformação lookup, responsável por combinar dois inputs em comum através de mapeamentos, relacionando os dados de uma origem com um DataSet, possibilitando popular as colunas código loja, código cliente, código veículo e código tempo na tabela fato_venda. Por fim, foi
aplicado o componente OLE DB Destination que vincula ao data warehouse para o armazenamento dos dados.

## Desenvolvimento dos Cubos:
A próxima etapa do processo businesses Intelligence foi o desenvolvimento de cubos OLAP, utilizando a ferramenta SQL Server Analysis
Services (SSAS).

<sub>*BI-Concessionaria-de-carros/Analise_Multidimensional_Concessionaria/*</sub>

## Desenvolvimento dos Dashboards:
Após ter passado pela obtenção de dados, tratamento, carregamento a fim de tornar os dados limpos e coerentes, a última etapa do processo BI é a visualização dos dados que possam responder as questões levantadas nas necessidades do negócio.

## Resultados Obtidos:






