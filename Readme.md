# 🍕 Data Warehouse & Dashboard Analítico — Vendas de Pizza

### BigQuery | Python | Modelagem Dimensional | Apache Superset (Preset)

![alt text](<Imagens/Captura de tela de 2025-12-12 15-42-10.png>)

![alt text](<Imagens/Captura de tela de 2025-12-12 15-42-23.png>)

![alt text](<Imagens/Captura de tela de 2025-12-12 15-42-40.png>)

![alt text](<Imagens/Captura de tela de 2025-12-12 15-42-56.png>)

### 📋 Visão Geral

Este repositório contém o projeto completo de um Data Warehouse dimensional para análise de vendas de uma pizzaria, incluindo:

- Modelagem estrela com tabelas fato e dimensões

- ETL organizado em notebooks e scripts Python

- Execução em Google BigQuery

- Criação de um dashboard analítico no Apache Superset (Preset)

- Pipeline simples, limpo e escalável para análises futuras

O objetivo deste projeto é transformar dados transacionais em insights estratégicos, permitindo análises temporais, de produto e de desempenho operacional.

### 🏗️ Arquitetura do Data Warehouse

 #### Tabela Fato

fact_pizza_sales
Contém as transações de vendas, incluindo quantidade, preço, horários e chaves estrangeiras para as dimensões.

#### Dimensões

dim_date — calendário completo com atributos analíticos

dim_time — classificação de períodos (horário, período, turno)

dim_pizza — catálogo completo de pizzas (SCD Type 1)

dim_order — pedidos consolidados

### 🔄 Modelagem

Este DW segue o padrão Kimball, garantindo performance nas consultas e clareza na análise.

### 🔧 Tecnologias Utilizadas

#### Data & ETL

- Google BigQuery

- Python (Pandas, BigQuery Client)

- Jupyter Notebooks

- dotenv para variáveis de ambiente

- SCD Type 1 para dimensões lentamente mutáveis

#### Dashboard & Visualização

- Apache Superset (Preset Cloud)
Dashboard profissional desenvolvido com:

- Gráficos de receita

- Volume por horário

- Pizza mais vendida

- Análises por período e sazonalidade

### 📊 Dashboard no Superset

- O projeto inclui um dashboard analítico desenvolvido no Preset (Apache Superset Cloud), com visualizações que aproveitam o DW:

- Receita por pizza

- Receitas por período do dia (meal period / shift)

- Análise temporal (dia, semana, mês, trimestre)

- Heatmap de volume por hora

- Tendência anual das vendas

- Análise de sazonalidade e comportamento de demanda

### 🛠️ Pipeline ETL

#### 1. Extração

- Dados brutos carregados no BigQuery.

#### 2. Transformação

- Limpeza, padronização e enriquecimento

- Conversão de tipos

- Criação de chaves substitutas

- Deduplicação

#### 3. Carga
Tabelas dimensão e fato carregadas no schema DW:

- DW.dim_date

- DW.dim_time

- DW.dim_pizza

- DW.dim_order

- DW.fact_pizza_sales

#### 4. Consumido pelo Superset

- O dashboard se conecta diretamente ao schema DW.