# Projeto A – Ingestão de Dados CRM

**Status:** Em produção  
**Última atualização:** 2025-06-10  
**Responsável:** Fulano da Silva

## Visão Geral

Pipeline responsável por ingestão incremental de dados do CRM para o Data Lake (S3), posterior tratamento e carga em Delta Lake no Databricks.

## Arquitetura

Ver [[Arquitetura]].

## Pipelines

- [[projeto-a/pipelines#ingestao-crm]]
- [[projeto-a/pipelines#tratamento]]
- [[projeto-a/pipelines#carga]]

## Fonte dos dados

- API REST CRM
- Extração incremental via `last_updated`

## Ferramentas utilizadas

- Airflow
- Databricks
- AWS S3
