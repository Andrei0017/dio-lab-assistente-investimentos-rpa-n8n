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

```text
[ Página Web de Clientes ] 
           │
           ▼ (Web Scraping / RPA com Python + BeautifulSoup)
[ Script Python: rpa/extrair_clientes.ipynb ]
           │
           ▼ (HTTP POST / JSON)
[ Webhook Trigger no n8n ]
           │
           ▼ (Requisição HTTP ao docs/data.csv)
[ Cruzamento de Dados & Regras de Negócio ]
           │
           ▼
[ Recomendações Personalizadas Geradas ]
