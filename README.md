# analise-exploratoria-de-dados-com-postgresql
Análise Exploratória do Brazilian E-Commerce Public Dataset do Olist realizado no postgreSQL.
Os dados foram incorporados na mesma estrutura encontrada no Kaggle, sem a transformação em um modelo dimensional dedido à análise de dados propriamente.
As consultas estão númeradas para identificar o resultado (ou amostragem) de cada uma.

## Objetivos
- Analisar a **estrutura e integridade** das tabelas do dataset  
- Investigar **valores extremos** e **métricas de vendas**
- Avaliar **tendências mensais** e **crescimento de vendas**  
- Mapear **categorias mais vendidas** e **distribuição geográfica dos clientes**  

## Sobre o Dataset
O [Olist E-commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) contém informações de 100 mil pedidos feitos entre 2016 e 2018 em diversos marketplaces no Brasil. Foram utilizadas as seguintes tabelas para este estudo:
- Tabela de Clientes
- Tabela de Pedidos
- Tabela de Vendedores
- Tabela de Produtos

## Ferramentas
- **PostgreSQL** – Banco de dados relacional para armazenar e consultar os dados  
- **pgAdmin 4** – Ambiente gráfico para execução das consultas  
- **SQL** – Linguagem de análise e manipulação dos dados  

# Consultas Realizadas

## Entendimento Geral
O objetivo é uma sumarização inicial e ter noção do volume e integridade. Devido a natureza lógica original do dataset dificilmente apresentaria inconsistências de integridade referencial, duplicidades indevidas ou valores órfãos.
| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 1 | **Tamanho e integridade de cada tabela** | Verifica o número de registros e checa possíveis inconsistências entre as tabelas do dataset. |
| 2 | **Maior e menor valor de pedidos** | Identifica o pedido mais caro e o mais barato do histórico de vendas. |
| 3 | **Total de pedidos e valor total vendido** | Identifica o volume total de pedidos e o faturamento agregado de todo período. |

## Análise Financeira
Alguns consultas retornam valores gerais que englobam todos os registros históricos e outras são específicas para um recorde no tempo específico.
| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 4 | **Ticket médio por pedido** | Calcula o valor médio gasto por pedido no dataset em todo período. |
| 5 | **Receita e ticket médio mês a mês para o ano 2017)** | Analisa a evolução da receita e ticket médio ao longo de 2017. |
| 6 | **Quantidade de pedidos por mês (ordenado por valor total)** | Ordena os meses conforme o faturamento total em relação a todo período. |
| 7 | **Crescimento mensal das vendas (2017)** | Mede o crescimento percentual (em relação ao mês anrterior) das vendas mês a mês em 2017. |

## Análise de Produto
| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 8 | **Quantidade de pedidos por categoria** | Retorna a quantidade de pedidos realizados por categoria de produto. |
| 9 | **Valor total de vendas por categoria** | Retorna o faturamento total de cada categoria. |

## Análise Geográfica
| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 10 | **Quantidade de clientes por estado** | Mostra a distribuição de clientes em todos os estados cadastrados. |
| 11 | **Ranking de cidades por cada estado por quantidade de clientes** | Classifica as cidades dos estados com base na quantidade de clientes que possui. |
| 12 | **Top 3 cidades com mais clientes por estado** | Exibe as três cidades com maior concentração de clientes por estado. |

## Distribuições
O objetivo é aplicar técnicas para obter resumos estatísticos e identificar padrões de concentração de vendas, receitas e quantidade de pedidos realizados por clientes. 
Foi identificado que o dataset presente é extremamente assimétrico em alguns casos, deixando em aberto a aplicação de outras técnicas mais recomendadas para este cenário.

| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 13 | **Distribuição da Receita por Vendedor** | Mostra como a receita total está distribuída entre os vendedores, destacando concentração de faturamento. |
| 14 | **Distribuição de Pedidos por Cliente** | Analisa quantos pedidos cada cliente realizou, permitindo identificar clientes ocasionais e recorrentes. |
| 15 | **Distribuição em Percentual por Quantidade de Pedidos por Cliente** | Calcula a proporção exata (em %) de clientes que realizaram 1, 2, 3 ou mais pedidos. |
| 16 | **Distribuição da Quantidade de Pedidos por Cliente por Estado** | Segmenta a quantidade de clientes por quantidade de pedidos realizados (com porcentagem). |
| 17 | **Distribuição da Quantidade de Pedidos por Cliente por Estado apenas para Clientes Recorrentes (2 pedidos ou mais)** | Restringe a análise aos clientes fiéis (com 2 ou mais pedidos) para avaliar concentração regional. |

## Detecção de Outliers
Outliers são valores atípicos, valores que se diferenciam muito da maioria do restante dos dados. Outliers não necessáriamente erros, mas uma análise sobre estes dados podem ajudar a identificar anomalias que não deveriam existir e estão influenciando nas análises estatísticas dos dados.

Visto que o dataset é extremamente assimétrico, a utilização de técnica baseada em média e desvio padrão talvez não seja a mais recomendada para se obter resultados sobre outliers para este caso. Por isso foi utilizado um valor maior que o normal como escala para definir o que seriam valores discrepantes. 

Estas consultas SQL tem como objetivo identificar e avaliar a dispersão de valores, explorando métricas estatísticas e percentis para detectar padrões em preços e pedidos.

| # | Título da Consulta | Descrição |
|:-:|--------------------|------------|
| 18 | **Detectando Outliers em Colunas Numéricas** | Identifica valores atípicos em variáveis numéricas (preço e frete) com base na média e desvio padrão. |
| 19 | **Detectando Outliers com Base no Valor Total dos Pedidos** | Analisa o valor total de cada pedido para encontrar pedidos fora do padrão |
| 20 | **Top 0.5% Compradores** | Retorna os pedidos mais caros, correspondendo ao Top 0.5%, para investigar outliers extremos e identificar clientes de alto valor. |


## Fim
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?logo=postgresql&logoColor=white)
[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=fff)](#)
