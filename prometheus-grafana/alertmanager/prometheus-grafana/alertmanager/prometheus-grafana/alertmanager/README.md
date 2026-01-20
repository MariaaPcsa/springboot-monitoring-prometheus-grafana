Projeto Prometheus-Grafana - Monitoramento de Aplicações

Este projeto foi desenvolvido em aula da **Alura**, como prática de monitoramento de aplicações Java com **Spring Boot**, **Prometheus**, **Grafana** e **Alertmanager**.  

O objetivo é demonstrar a integração entre uma API Spring Boot, coleta de métricas, armazenamento de dados e alertas, usando containers Docker.

---

## Estrutura do projeto

- `app/` → código-fonte da API Spring Boot (forum-api)
- `client/` → código-fonte do cliente (frontend)
- `prometheus/` → configuração do Prometheus e regras de alertas
- `grafana/` → dados persistentes do Grafana e dashboards
- `alertmanager/` → configuração do Alertmanager
- `nginx/` → configuração do proxy reverso
- `mysql/` → scripts de inicialização do banco MySQL
- `.env` → variáveis de ambiente (não versionado)

---

## Tecnologias usadas

- Java 21 + Spring Boot
- H2 Database / MySQL
- Redis
- Prometheus
- Grafana
- Alertmanager
- Docker / Docker Compose
- Nginx (proxy reverso)

---

## Configuração de ambiente

Todas as variáveis sensíveis devem ser definidas no arquivo `.env` (não incluído no repositório por segurança):

```env
# Banco de dados
DB_USERNAME=...
DB_PASSWORD=...
MYSQL_HOST=...
MYSQL_DB=...
MYSQL_USER=...
MYSQL_PASSWORD=...

# Redis
REDIS_HOST=...
REDIS_PORT=...

# JWT
JWT_SECRET=...
JWT_EXPIRATION=86400000

# Grafana
GRAFANA_ADMIN_USER=...
GRAFANA_ADMIN_PASSWORD=...
GRAFANA_PORT=3000

# Spring Boot
SPRING_PORT=8080

# Alertmanager
ALERTMANAGER_PORT=9093

# Slack webhook
SLACK_WEBHOOK_URL=...
Como rodar o projeto
No diretório raiz do projeto, execute:

1️⃣ Subir todos os containers:

docker compose up -d
2️⃣ Verificar se os containers estão rodando:

docker ps
3️⃣ Logs em tempo real da aplicação:

docker compose logs -f app-forum-api
4️⃣ Parar o projeto e limpar volumes:

docker compose down --volumes --remove-orphans
Endpoints principais
Spring Boot health: http://localhost:8080/actuator/health

Grafana: http://localhost:3000 (usuário: admin / senha: admin)

Prometheus: http://localhost:9090

Alertmanager: http://localhost:9093

Dashboards
Você pode importar dashboards prontos da comunidade do Grafana:

Spring Boot 2.1 System Monitor

Outros dashboards podem ser importados pelo ID ou JSON.

Alertmanager
Configura alertas do Prometheus e envia notificações para canais como Slack.
Todos os secrets (webhook, tokens) devem ser configurados via .env.

Exemplo de rota de alerta:

route:
  group_by: [app, group, env]
  receiver: 'ops-forum-api'
Boas práticas
Nunca versionar arquivos com secrets (.env, comandos.txt).

Teste alertas e dashboards localmente antes de usar em produção.

Use variáveis de ambiente para todos os dados sensíveis.

Sempre limpar volumes e containers órfãos ao atualizar o projeto.

Créditos
Projeto criado durante aulas da Alura como prática de monitoramento de aplicações com Spring Boot e observabilidade.
