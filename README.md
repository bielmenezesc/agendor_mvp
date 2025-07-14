# 🤖 AI Sales Agent Automation (n8n + Qdrant + MongoDB)

Este projeto implementa um **AI Agent inteligente** para automatizar interações em linguagem natural com o CRM Agendor, utilizando **n8n**, **Qdrant**, **MongoDB** e **OpenAI API**.

---

## 🚀 Funcionalidades

- Processamento de mensagens em linguagem natural.
- Resolução de ambiguidades via IA.
- Aplicação de regras de negócio antes de ações.
- Busca semântica de entidades usando Qdrant.
- Registro de todas interações em MongoDB.
- Orquestração total via n8n.
- Exposição de um endpoint de consulta de logs via webhook.

---

## 📦 Stack Tecnológica

- [n8n](https://n8n.io/) — Orquestrador principal.
- [Qdrant](https://qdrant.tech/) — Banco vetorial (busca semântica).
- [MongoDB](https://www.mongodb.com/) — Log e armazenamento histórico.
- [OpenAI API](https://platform.openai.com/) — Compreensão de linguagem.
- Docker Compose — Ambiente local unificado.

---

## ⚙️ Como Subir o Projeto

1. **Clone o repositório** e acesse a pasta do projeto:

```bash
git clone <seu-repo>
cd seu-projeto
```

2. **Suba os containers:**

```bash
docker-compose up -d
```

3. **Acesse o n8n:**

- URL: [http://localhost:5678](http://localhost:5678)
- Usuário: `admin`
- Senha: `admin`

---

## 📥 Importação dos Workflows

1. Dentro do painel do n8n, clique em **Import Workflow**.
2. Importe os arquivos `.json` localizados na pasta `/workflows` deste projeto.
3. Publique os fluxos conforme desejar.

---

## 🔗 Conexões Internas no n8n

- **MongoDB:**

  - Host: `mongodb`
  - Porta: `27017`
  - Database: `logs` (ou nome de sua escolha)
  - Autenticação: desabilitada

- **Qdrant API:**

  - Base URL: `http://qdrant:6333`

**Observação:** estas configurações devem ser criadas nas Credenciais do n8n.

---

## 📊 API de Logs (Webhook)

O projeto expõe um **endpoint REST** via workflow no próprio n8n para consulta de logs:

- **Endpoint:**
  `GET http://localhost:5678/webhook/logs`

- **Parâmetros suportados (Query String):**

  - `company` (opcional)
  - `user` (opcional)
  - `from` (opcional, ISO date)
  - `to` (opcional, ISO date)

**Exemplo:**

```
GET http://localhost:5678/webhook/logs?company=Acme
```

O endpoint retorna histórico filtrado em formato JSON.

---

## 📁 Estrutura do Projeto

```
/seu-projeto/
├── docker-compose.yml
├── README.md
├── workflows/
│   └── ai_agent_workflow.json
│   └── log_api_workflow.json
```

---

## ✅ Considerações

- O agente mantém contexto de conversação.
- Todas as interações são logadas automaticamente no MongoDB.
- O sistema lida com ambiguidades e solicitações incompletas.
- Componentes 100% locais usando Docker.

---

## 🛠️ Requisitos

- Docker + Docker Compose
- Editor para workflows do n8n (acesso via navegador)

---

## 📞 Suporte

Para dúvidas ou sugestões, entre em contato:
**[bielmenezesc@gmail.com](mailto:bielmenezesc@gmail.com)**
