# 🤖 Assistente de Investimentos com RPA e IA Generativa no n8n

> Projeto desenvolvido para o Desafio de Projeto da **DIO (Digital Innovation One)**: criando um assistente de investimentos automatizado com extração via RPA em Python e orquestração de workflow no n8n.

---

## 🎯 Objetivo do Projeto

Construir um pipeline completo de automação inteligente voltado para o setor financeiro:
1. **Extração (RPA):** Coletar dados cadastrais de clientes fictícios (nome, email, saldo e perfil) a partir de uma página web usando Python e BeautifulSoup.
2. **Orquestração (N8N):** Receber as informações via Webhook, processar os dados e cruzar os perfis de investidor com a base de investimentos (`data.csv`).
3. **Recomendações Personalizadas:** Gerar automaticamente mensagens direcionadas para cada cliente de acordo com seu perfil de risco (Conservador, Moderado e Arrojado).

---

## 🏗️ Arquitetura da Solução

O fluxo da automação funciona na seguinte sequência:
- **Passo 1:** Página Web com a tabela de clientes fictícios.
- **Passo 2:** Script Python (`rpa/extrair_clientes.ipynb`) que faz web scraping com BeautifulSoup e envia via HTTP POST.
- **Passo 3:** Webhook Trigger no n8n recebe os dados dos clientes.
- **Passo 4:** Requisição HTTP lê o arquivo de produtos de investimento (`docs/data.csv`).
- **Passo 5:** O nó de código cruza o perfil do cliente e gera a recomendação personalizada.

---

## 📁 Estrutura do Repositório

- `rpa/extrair_clientes.ipynb`: Notebook Python responsável pela automação de raspagem dos clientes e envio via requisição POST ao webhook.
- `n8n/workflow.json`: Exportação completa do fluxo do n8n com o nó de Webhook, busca de dados do CSV e geração lógica das recomendações personalizadas.
- `docs/index.html`: Página web de simulação com a tabela de clientes.
- `docs/data.csv`: Catálogo com as opções de investimento segmentadas por perfil de risco.

---

## ⚙️ Regras de Recomendação por Perfil

- **Conservador:** Foco em preservação de capital e liquidez (ex: Tesouro Selic, CDB 100% CDI).
- **Moderado:** Estratégia mista buscando ganho real com controle de volatilidade (ex: Fundos Imobiliários e Tesouro IPCA+).
- **Arrojado:** Maximização de rentabilidade no longo prazo (ex: Ações, ETFs internacionais e Fundos Multimercado).

---

## 🚀 Como Executar o Projeto

1. **Executar o n8n:**
   - Importe o arquivo `n8n/workflow.json` na sua instância do n8n.
   - Ative o fluxo para deixar o Webhook receptivo.

2. **Executar o RPA:**
   - Abra o notebook `rpa/extrair_clientes.ipynb` (no Jupyter ou Google Colab).
   - Execute todas as células para raspar a página de clientes e disparar os dados para o endpoint do n8n.
