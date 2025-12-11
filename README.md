# n8n-compose

Este repositório contém uma stack Docker completa para executar o [n8n](https://n8n.io/) em ambiente de produção, com alta disponibilidade, autenticação, banco de dados PostgreSQL, Redis para filas, e proxy reverso Nginx com suporte a SSL (Let's Encrypt).

## Estrutura dos Arquivos

- **docker-compose.yaml**: Orquestra os serviços (n8n, worker, webhook, PostgreSQL, Redis) e volumes persistentes.
- **.env**: Variáveis de ambiente sensíveis e de configuração.
- **nginx-n8n.conf**: Configuração do Nginx para servir o editor do n8n via HTTPS.
- **nginx-webhook.conf**: Configuração do Nginx para servir webhooks do n8n via HTTPS.

## Serviços

- **n8n (editor)**: Interface principal do n8n.
- **n8n (webhook)**: Serviço dedicado para webhooks, melhorando performance e isolamento.
- **n8n (worker)**: Processamento de execuções em background (fila).
- **PostgreSQL**: Banco de dados relacional para persistência dos dados do n8n.
- **Redis**: Gerenciamento de filas para execuções distribuídas.
- **Nginx**: Proxy reverso, SSL e roteamento de domínios.

## Como usar

1. **Configure o arquivo `.env`** com suas variáveis (domínios, senhas, chaves, etc).
2. **Suba a stack**:
   ```powershell
   docker-compose up -d
   ```
3. **Configure o Nginx** usando os arquivos `nginx-n8n.conf` e `nginx-webhook.conf` no seu servidor.
4. **(Opcional) Configure SSL** com Let's Encrypt (Certbot).

## Exemplo de domínios
- Editor: [https://n8n.minhaempresa.com.br](https://n8n.minhaempresa.com.br)
- Webhook: [https://webhook.minhaempresa.com.br](https://webhook.minhaempresa.com.br)

## Segurança
- Autenticação básica ativada por padrão (usuário/senha no `.env`).
- Recomenda-se alterar as senhas e chaves antes de subir em produção.

## Créditos
- Baseado na documentação oficial do [n8n](https://docs.n8n.io/hosting/docker/).

---

> **Mantenedor:** Seu Nome — [seu@email.com]
