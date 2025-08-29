![alt text](cover.png)

## Visão Geral
Este projeto implementa uma plataforma moderna de engenharia de dados para um e-commerce que integra informações de vendas online, lojas físicas e interações de usuários em tempo real.

A arquitetura foi construída sobre serviços da AWS, com Apache Airflow para orquestração, Databricks para processamento de dados, Terraform para IaC, Kubernetes (EKS) para escalabilidade e Power BI para consumo de relatórios e dashboards.
## Objetivos
- Ingestão de dados batch (ERP, CRM, RDS).
- Ingestão de dados streaming (eventos de site/app em tempo real).
- Construção de um Data Lakehouse baseado em camadas Bronze, Prata e Ouro.
- Modelo dimensional (Star Schema) para análise de negócios.
- Visualização e análise dos dados no Power BI.
- Infraestrutura provisionada e gerenciada via Terraform.
- Orquestração resiliente via Airflow em Kubernetes.
## Tecnologias
Ingestão de Dados
- Batch:
  - AWS RDS (MySQL/Postgres) – dados transacionais.
  - Arquivos CSV/Parquet – importados via S3.
  - Airflow (EKS) – orquestra jobs ETL de ingestão em lote.
- Streaming:
  - AWS Kinesis Data Streams – eventos de clique, navegação e carrinho.
  - AWS Kinesis Firehose – grava dados crus no S3 (Bronze) e envia para Databricks.

Processamento e Transformação
- Databricks (Delta Lake):
  - Batch: transformação de dados históricos.
  - Streaming: enriquecimento em tempo quase real.
- Camadas:
  - Bronze → dados crus.
  - Prata → dados tratados e normalizados.
  - Ouro → modelo dimensional (Star Schema).
- Modelo Dimensional (Star Schema):
  - Fato_Vendas (transações).
  - Dim_Cliente,
  - Dim_Produto,
  - Dim_Tempo, 
  - Dim_Loja, 
  - Dim_Canal.

Armazenamento
- Amazon S3 dividido em:
  - /bronze – dados crus.
  - /silver – dados limpos.
  - /gold – dados analíticos (modelo dimensional).
- Delta Lake sobre S3 para versionamento e transações ACID.

Consumo e Visualização
- Athena ou Redshift Spectrum → consultas SQL.
- Power BI → dashboards analíticos.
  - Vendas por canal (online vs físico).
  - Performance de campanhas em tempo real.
  - Análise de clientes (novos x recorrentes).

Infraestrutura e Orquestração
- Terraform:
  - Criação de buckets S3 (bronze, prata, ouro).
  - Provisionamento de clusters EKS (Airflow).
  - Criação de Kinesis, RDS, permissões IAM.
  - Deploy do workspace Databricks.
- Kubernetes (EKS):
  - Airflow rodando em containers.
  - Escalabilidade horizontal automática.
  - Integração com AWS Secrets Manager.
- Monitoramento:
  - CloudWatch + Prometheus → métricas.
  - Airflow UI → monitoramento de DAGs.
  - Databricks Jobs → status de pipelines.
## Arquitetura
![alt text](architecture.png)
## Documentações Utilizadas
#
#
#
![alt text](cover.png)

## Overview
## Objectives
## Technologies
## Architecture
![alt text](architecture.png)
## Documentation Used