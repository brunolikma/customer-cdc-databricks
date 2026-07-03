🚀 Customer CDC Streaming Platform
📌 Visão Geral

Este projeto simula uma plataforma moderna de dados em tempo real para ingestão, processamento e análise de eventos de clientes utilizando arquitetura orientada a eventos (CDC - Change Data Capture).

A solução foi projetada para demonstrar práticas reais de Engenharia de Dados em ambientes distribuídos, com foco em streaming, escalabilidade, qualidade de dados e arquitetura Medallion, utilizando Apache Spark Structured Streaming no Databricks.

🎯 Objetivo do Projeto

Construir um pipeline de dados end-to-end capaz de:

Simular eventos de clientes (INSERT, UPDATE, DELETE)
Ingerir dados em tempo real via streaming
Processar dados utilizando Spark Structured Streaming no Databricks
Aplicar arquitetura Medallion (Raw → Bronze → Silver → Gold)
Garantir consistência e qualidade dos dados via processamento incremental
Disponibilizar dados prontos para consumo analítico
🧠 Problema de Negócio Simulado

Em cenários reais, sistemas de CRM e plataformas digitais geram constantemente alterações em registros de clientes.

Essas mudanças precisam ser capturadas em tempo real para permitir:

Análise de comportamento de clientes
Atualização de dashboards quase em tempo real
Segmentação dinâmica de usuários
Consistência entre sistemas analíticos e transacionais

Este projeto simula esse cenário utilizando dados gerados por CDC.

🏗️ Arquitetura da Solução
Faker CDC Generator
        │
        ▼
Kafka (Event Streaming)
        │
        ▼
Databricks (Spark Structured Streaming)
        │
        ▼
RAW Layer (Data Lake)
        │
        ▼
BRONZE Layer (Structured Data)
        │
        ▼
SILVER Layer (Consolidated State - MERGE)
        │
        ▼
GOLD Layer (Analytics Ready Data)

🧱 Arquitetura Medallion

🟤 RAW Layer
Armazena eventos exatamente como recebidos
Dados imutáveis
Fonte única da verdade para reprocessamento

🟡 BRONZE Layer
Dados estruturados e tipados
Parsing de JSON
Inclusão de metadados de ingestão
Preparação para transformações

⚪ SILVER Layer
Aplicação de regras de negócio
Deduplicação
Processamento de CDC (INSERT, UPDATE, DELETE)
Uso de MERGE para estado atual do cliente
Aplicação de soft delete

🟢 GOLD Layer
Dados agregados e analíticos
Otimizado para consumo por BI e Analytics
Métricas de negócio

Exemplos:
Clientes ativos
Clientes por estado/cidade
Taxa de crescimento de cadastros
Evolução temporal de eventos

⚙️ Tecnologias Utilizadas
Python 3.10+
Apache Spark (Structured Streaming)
Databricks
Delta Lake
Kafka
AWS S3
Faker (geração de dados)
GitHub Actions (CI/CD)
Pytest (testes)

📁 Estrutura do Projeto
customer-cdc-databricks/

.github/              → CI/CD pipelines (GitHub Actions)
configs/              → Configurações centralizadas
docs/                 → Documentação e arquitetura
producer/             → Gerador de eventos CDC (Faker)
src/
  common/             → Utilitários compartilhados
  raw/                → Ingestão inicial (streaming)
  bronze/             → Transformação estrutural
  silver/             → Processamento CDC (MERGE)
  gold/               → Camada analítica
tests/                → Testes automatizados
notebooks/            → Execução no Databricks
requirements.txt      → Dependências do projeto
README.md             → Documentação principal


🔄 Modelo de Dados (CDC)

Exemplo de evento gerado:

{
  "event_id": "uuid",
  "customer_id": 123,
  "operation": "UPDATE",
  "event_timestamp": "2026-07-03T12:00:00Z",
  "payload": {
    "name": "Bruno Lima",
    "email": "bruno@email.com",
    "city": "Praia Grande"
  }
}

Operações suportadas:

INSERT → criação de cliente
UPDATE → atualização de dados
DELETE → inativação (soft delete)

📊 Principais Conceitos Demonstrados

Este projeto aplica conceitos avançados de engenharia de dados:

Arquitetura Medallion
Change Data Capture (CDC)
Streaming com Spark Structured Streaming
Processamento incremental
Delta Lake (ACID Transactions)
MERGE INTO (upsert)
Data Lake em cloud (S3)
Separação por camadas (Raw / Bronze / Silver / Gold)
Engenharia de dados orientada a eventos

🚀 Roadmap do Projeto
 Estrutura inicial do projeto
 Geração de dados CDC (Faker)
 Streaming com Kafka
 Ingestão no Databricks (Raw Layer)
 Construção Bronze Layer
 Implementação Silver Layer (MERGE CDC)
 Criação Gold Layer (Analytics)
 Data Quality Framework
 CI/CD com GitHub Actions
 Dashboard final no Databricks SQL

🧪 Testes

O projeto inclui:

Testes de transformação de dados
Validação de schema
Testes de lógica de CDC
Validação de regras de qualidade

📌 Diferencial do Projeto

Este projeto foi desenhado para simular um ambiente real de engenharia de dados, com foco em:

Escalabilidade
Processamento em tempo real
Boas práticas de arquitetura
Separação clara de responsabilidades
Pipeline completo de dados (end-to-end)

👨‍💻 Autor
Projeto desenvolvido como parte de estudos avançados em Engenharia de Dados, com foco em:

Databricks
Streaming de dados
Arquitetura de Data Lake moderno
Pipelines de dados em produção

📌 Observação

Este projeto é totalmente simulado e tem fins educacionais, com o objetivo de demonstrar competências em engenharia de dados moderna.