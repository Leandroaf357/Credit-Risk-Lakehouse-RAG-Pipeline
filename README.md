# Credit-Risk-Lakehouse-RAG-Pipeline
Pipeline de engenharia de dados ponta a ponta construído na Arquitetura Medalhão (Databricks), combinando processamento distribuído com PySpark, gerenciamento de infraestrutura via Databricks Asset Bundles (DABs) e um sistema de Busca Semântica (RAG) utilizando FAISS e Hugging Face.
<p align="center">
  <h1 align="center">🚀 Credit Risk Lakehouse & RAG Intelligence Pipeline</h1>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white" alt="Databricks">
  <img src="https://img.shields.io/badge/Apache%20Spark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white" alt="Spark">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Delta%20Lake-009688?style=for-the-badge&logo=deltalake&logoColor=white" alt="Delta Lake">
  <img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black" alt="Hugging Face">
  <img src="https://img.shields.io/badge/LangChain-1C3C3C?style=for-the-badge&logo=chainlink&logoColor=white" alt="LangChain">
</p>

<p align="center">
  <b>Pipeline de Engenharia de Dados End-to-End com Arquitetura Medalhão e Assistente RAG Inteligente.</b>
</p>

---

## 🎯 Sobre o Projeto

Este projeto implementa uma solução completa de **Lakehouse e Inteligência Artificial** para análise de risco de crédito. O pipeline processa dados brutos de empréstimos, limpa e modela as informações através das camadas do Delta Lake, e disponibiliza um motor de **Busca Semântica (RAG)** integrado a Large Language Models (LLMs) open-source de forma resiliente.

---

## 🏛️ Arquitetura do Pipeline (Medallion Architecture)

O fluxo de dados segue rigorosos padrões de engenharia, garantindo rastabilidade e performance:

```text
[ Landing Zone / CSV ] 
        │
        ▼
   🥉 Bronze Layer  ──> Ingestão bruta preservando o formato original (Delta)
        │
        ▼
   🥈 Silver Layer  ──> Limpeza, tipagem, tratamento de nulos e modelagem relacional
        │
        ▼
   🥇 Gold Layer    ──> Agregações de negócio, métricas e sumarização textual para IA
        │
        ▼
   🤖 RAG & FAISS   ──> Indexação vetorial e Geração de Respostas Humanizadas (LLM)
✨ Principais Funcionalidades
Processamento Distribuído: Utilização de PySpark e Spark SQL para manipulação eficiente de grandes volumes de dados.

Infraestrutura como Código (IaC): Orquestração e automação de deploys utilizando Databricks Asset Bundles (DABs).

Motor de Busca Semântica (RAG): Indexação de resumos analíticos da camada Gold utilizando FAISS e embeddings de alta performance (all-MiniLM-L6-v2).

Resiliência e Fallback: Sistema inteligente de múltiplas tentativas (fallbacks) para consumo de LLMs via API do Hugging Face, garantindo que o pipeline nunca quebre por indisponibilidade de provedores externos.

credit-risk-pipeline/
├── resources/
│   └── credit_risk_job.yml     # Orquestração de Jobs via Asset Bundles
├── src/
│   ├── setup/
│   │   ├── 00_setup_infraconfig.sql # Configuração de catálogos e schemas
│   │   └── 05_vector_search_setup.py# Pipeline RAG (FAISS + Hugging Face)
│   ├── bronze/
│   │   └── 01_ingestao_bronze.py    # Ingestão de dados brutos
│   ├── silver/
│   │   └── 02_transformacao_silver.py# Limpeza e refinamento
│   └── gold/
│       ├── 03_agregacao_gold.py     # Tabelas fato e dimensão agregadas
│       └── 04_gold_rag_text.py      # Criação dos chunks textuais para IA
└── README.md
