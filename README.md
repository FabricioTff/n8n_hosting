# 🧩 n8n Docker Environment with Workers and PostgreSQL

Este repositório fornece uma configuração pronta para uso do [n8n](https://n8n.io/) com suporte a **workers em fila**, **persistência com PostgreSQL** e **redis para controle de filas**, utilizando **Docker Compose**.

## 📦 Estrutura

- `docker-compose.yml`: Define os serviços `n8n`, `n8n-worker`, `postgres` e `redis`.
- `init-data.sh`: Script de inicialização que cria um usuário não-root no banco de dados PostgreSQL.
- `.env`: Exemplo de arquivo `.env` com as variáveis de ambiente necessárias para configurar os containers.

---

## 🚀 Como usar

### 1. Clone o repositório

```bash
git clone https://github.com/FabricioTff/n8n_hosting.git
cd n8n_hosting
```

### 2. Configure as variáveis de ambiente

Copie o arquivo `.env` de exemplo e ajuste os valores conforme necessário:

```bash
cp .env variables.env 
```

> ⚠️ Atenção: Não use valores vazios para `POSTGRES_PASSWORD` e `N8N_ENCRYPTION_KEY`.

### 3. Suba os containers

```bash
docker compose up --env-file variables.env -d
```

O n8n estará acessível em: [http://localhost:5678](http://localhost:5678)

---

## 🧠 Componentes

| Serviço      | Função                                                       |
|--------------|--------------------------------------------------------------|
| `n8n`        | Interface principal do n8n e orquestrador das execuções.     |
| `n8n-worker` | Worker em modo `queue` que processa execuções em background. |
| `postgres`   | Banco de dados relacional usado pelo n8n.                    |
| `redis`      | Gerenciador de filas de execução (Bull).                    |

---

## 🛠 Personalização

Você pode alterar os parâmetros no `variables.env` para adaptar ao seu ambiente, como:
- Porta de acesso ao n8n
- Credenciais do PostgreSQL
- Chave de criptografia do n8n (`N8N_ENCRYPTION_KEY`)
