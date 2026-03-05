# globalretractionwatch-crossmark-form
Interactive data visualization for Retraction Watch data and a friendly, secure, server-to-server Crossmark XML depositor for publishers.

# 🌐 Global Retraction Watcher & Crossmark Depositor
(English description)

# 🌐 Retraction Explorer & Crossmark Depositor

![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)
![PHP 8.3](https://img.shields.io/badge/PHP-8.3-blue.svg)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange.svg)
![UiKit](https://img.shields.io/badge/UI-UiKit-pink.svg)

An open-source interactive dashboard for global analysis of retracted scientific articles, integrated with a secure tool for generating XML and automatically depositing update metadata (Retractions, Corrections, etc.) via **Crossref / Crossmark**.

Analytical data is fed daily from the public **Retraction Watch** database.

---

## ✨ Key Features

### 1. Global Analytics Dashboard
* **Automated Synchronization (Cron):** Daily ingestion of tens of thousands of records from the Retraction Watch CSV directly into an optimized MySQL database.
* **Choropleth Map (Leaflet):** Interactive visualization of the global geographic distribution of retractions, dynamically colored via data join with GeoJSON.
* **Dynamic CSS Metrics:** Donut charts generated purely with CSS `conic-gradient`, with no heavy JS library dependencies.
* **Cascading Advanced Search:** Asynchronous filters (Continent -> Country) processed via an internal PHP API, returning instant results in paginated tables.

### 2. Crossmark Deposit Module
* **Automated DOI Fetching:** Fetch API integration with the public Crossref API (`api.crossref.org`) to autofill original article metadata.
* **XML Generation:** Robust creation of the XML tree in the official Crossref `4.3.7` standard using PHP's native `DOMDocument` class.
* **Secure Proxy via cURL:** Encrypted transmission (TLS/SSL) of the XML and credentials directly to the Crossref deposit endpoint (`doi.crossref.org/servlet/deposit`).
* **File Control:** Allows copying the XML to the clipboard or downloading the generated `.xml` file locally via `Blob` and `URL.createObjectURL`.

---

## 🛠️ Tech Stack

* **Backend:** PHP 8.3 (PDO, cURL, DOMDocument)
* **Database:** MySQL / MariaDB
* **Frontend:** Vanilla JavaScript (ES6+), HTML5, CSS3
* **UI Framework:** UiKit 3
* **Maps:** Leaflet.js
* **API Integrations:** Crossref REST API

---

## 📁 Architecture and Security

The project uses a "Public Directory" pattern to ensure that database credentials and backend routines are never exposed to the internet.

```text
my_project/
├── cron/                   # [Private] Automation scripts
│   └── sync_retractions.php
├── database/               # [Private] Database modeling
│   └── schema.sql
├── src/                    # [Private] Business logic and credentials
│   └── config.php          # -> Insert your DB credentials here
└── public/                 # [Public] Web Server Document Root
    ├── index.php           # Dashboard Analytics
    ├── deposito.php        # Crossmark Tool
    ├── css/
    ├── js/
    └── api/                # Internal endpoints (JSON)
        ├── buscar_resultados.php
        ├── depositar_crossref.php
        ├── gerar_xml.php
        ├── get_metricas_mapa.php
        └── get_totais_cards.php
```

# 🌐 Global Retraction Watcher & Crossmark Depositor
(Portuguese description)

![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)
![PHP 8.3](https://img.shields.io/badge/PHP-8.3-blue.svg)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange.svg)
![UiKit](https://img.shields.io/badge/UI-UiKit-pink.svg)

Um painel interativo de código aberto para análise global de artigos científicos retratados, integrado a uma ferramenta segura para geração de XML e depósito automático de metadados de atualização (Retratações, Correções, etc.) via **Crossref / Crossmark**.

Os dados analíticos são alimentados diariamente a partir da base pública do **Retraction Watch**.

---

## ✨ Funcionalidades Principais

### 1. Painel Analítico Global (Dashboard)
* **Sincronização Automatizada (Cron):** Ingestão diária de dezenas de milhares de registros do CSV do Retraction Watch diretamente para um banco de dados MySQL otimizado.
* **Mapa Coroplético (Leaflet):** Visualização interativa da distribuição geográfica global de retratações, pintada dinamicamente via união de dados (Data Join) com GeoJSON.
* **Métricas Dinâmicas em CSS:** Gráficos de rosca (Donuts) gerados puramente com CSS `conic-gradient`, sem dependências pesadas de bibliotecas JS.
* **Busca Avançada em Cascata:** Filtros assíncronos (Continente -> País) processados via PHP API interna, retornando resultados instantâneos em tabelas paginadas.

### 2. Módulo de Depósito Crossmark
* **Coleta Automática via DOI:** Integração via Fetch API com a API pública da Crossref (`api.crossref.org`) para autopreenchimento de metadados de artigos originais.
* **Geração de XML:** Criação robusta da árvore XML no padrão oficial `4.3.7` da Crossref utilizando a classe nativa `DOMDocument` do PHP.
* **Proxy Seguro via cURL:** Transmissão criptografada (TLS/SSL) do XML e credenciais diretamente para o endpoint de depósito da Crossref (`doi.crossref.org/servlet/deposit`).
* **Controle de Arquivos:** Permite a cópia do XML para a área de transferência ou o download do arquivo `.xml` gerado localmente via `Blob` e `URL.createObjectURL`.

---

## 🛠️ Stack Tecnológico

* **Backend:** PHP 8.3 (PDO, cURL, DOMDocument)
* **Banco de Dados:** MySQL / MariaDB
* **Frontend:** Vanilla JavaScript (ES6+), HTML5, CSS3
* **Framework de Interface:** UiKit 3
* **Mapas:** Leaflet.js
* **Integrações de API:** Crossref REST API

---

## 📁 Arquitetura e Segurança

O projeto utiliza um padrão de "Diretório Público" para garantir que credenciais de banco de dados e rotinas de backend jamais fiquem expostas à internet.

```text
meu_projeto/
├── cron/                   # [Privado] Scripts de automação
│   └── sync_retractions.php
├── database/               # [Privado] Modelagem do banco de dados
│   └── schema.sql
├── src/                    # [Privado] Lógica de negócio e credenciais
│   └── config.php          # -> Insira suas credenciais do DB aqui
└── public/                 # [Público] Document Root do Servidor Web
    ├── index.php           # Dashboard Analytics
    ├── deposito.php        # Ferramenta Crossmark
    ├── css/
    ├── js/
    └── api/                # Endpoints internos (JSON)
        ├── buscar_resultados.php
        ├── depositar_crossref.php
        ├── gerar_xml.php
        ├── get_metricas_mapa.php
        └── get_totais_cards.php
