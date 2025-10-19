# Projeto de Análise de Sentimento do Mercado Financeiro via Web Scraping

![Status](https://img.shields.io/badge/status-concluído-green)
![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)
![Selenium](https://img.shields.io/badge/Selenium-4.10+-43B02A?logo=selenium)
![TextBlob](https://img.shields.io/badge/NLP-TextBlob-blue)

Este projeto demonstra um pipeline de dados completo construído do zero, desde a **coleta de dados não estruturados da web (web scraping)** até a análise e visualização. O objetivo é extrair manchetes de notícias sobre uma ação específica, quantificar o sentimento dessas notícias usando **Processamento de Linguagem Natural (NLP)** e analisar visualmente a relação entre o sentimento do mercado e o preço da ação.

O diferencial deste projeto é a autonomia na criação do dataset e a implementação de um **scraper robusto e resiliente** para contornar proteções anti-scraping em sites dinâmicos.

**Ativo Analisado:** Magazine Luiza (MGLU3.SA)

---

## 🚀 Arquitetura do Pipeline

O fluxo de trabalho foi estruturado em quatro etapas principais:

1.  **Coleta de Dados de Preços (Yahoo Finance):** Utilização da biblioteca `yfinance` para baixar o histórico de cotações da MGLU3.SA.

2.  **Web Scraping Robusto de Notícias (Investing.com):**
    *   Implementação de um scraper com **Selenium** e **BeautifulSoup** para extrair manchetes e datas de notícias do portal Investing.com.
    *   **Técnicas Avançadas:** O script utiliza `webdriver-manager` para a gestão automática do ChromeDriver e emprega técnicas de **camuflagem** de *user-agent* para simular um navegador humano, superando mecanismos de proteção anti-bot.

3.  **Análise de Sentimento (NLP com TextBlob):**
    *   Cada manchete coletada é processada. A biblioteca `TextBlob` é usada para calcular a **polaridade do sentimento** (de -1.0 para negativo a +1.0 para positivo).

4.  **Análise e Visualização (Pandas & Matplotlib):**
    *   As pontuações de sentimento são agregadas por dia (média diária) e combinadas com o histórico de preços.
    *   Um gráfico final com dois eixos Y é gerado para visualizar o preço de fechamento e o sentimento médio diário em um único cronograma.

---

## 🛠️ Tecnologias Utilizadas

*   **Linguagem:** Python
*   **Web Scraping:** `Selenium`, `BeautifulSoup4`, `webdriver-manager`
*   **Análise de Dados:** `Pandas`, `NumPy`
*   **NLP:** `TextBlob`
*   **Dados Financeiros:** `yfinance`
*   **Visualização:** `Matplotlib`
*   **Ambiente:** Jupyter Notebook (VS Code)

---

## ⚙️ Como Executar o Projeto

**1. Pré-requisitos:**
*   Python 3.9+ e Google Chrome instalados.

**2. Clone o repositório:**
```bash
git clone https://github.com/ramos-anderson/analise-sentimento-financeiro.git
cd analise-sentimento-financeiro

3. Crie o ambiente virtual e instale as dependências:
code
Bash
# Crie e ative o ambiente virtual
python -m venv venv
venv\Scripts\activate

# Instale as bibliotecas
pip install -r requirements.txt
4. Baixe os corpus da TextBlob (apenas na primeira vez):
code
Bash
python -m textblob.download_corpora
5. Abra e Execute o Notebook:
Abra o arquivo analise_sentimento.ipynb em um ambiente Jupyter. Execute as células em ordem. A célula de scraping pode levar alguns segundos para rodar, pois irá iniciar uma instância do Chrome.