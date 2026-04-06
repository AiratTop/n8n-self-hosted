# AGENTS.md

## Purpose
Public self-hosted deployment template for scalable n8n automation stack (queue mode).

## Repository Role
- Category: `*-self-hosted` (public GitHub repository).
- Related local stack: `../n8n-docker`.
- Main entrypoint: `docker-compose.yml`.

## Stack Summary
- Services: `caddy`, `n8n-redis`, `n8n-psql`, `n8n-master`, `n8n-worker`.
- Exposed ports: `80`, `443/tcp`, `443/udp`, `5678`.
- External network: `shared_network`.
- Execution mode: `EXECUTIONS_MODE=queue`.

## Data and Config
- n8n data: `./data/n8n`.
- Redis data: `./data/n8n-redis`.
- PostgreSQL data: `./data/n8n-psql`.
- Local workflow files: `./local_files`.
- Reverse proxy config: `./config`.

## Operations
- First start helper: `./start-docker.sh`.
- Restart stack: `./restart-docker.sh`.
- Update images and restart: `./update-docker.sh`.
- Backup helper: `./backup.sh`.
- Caddy reload helper: `./caddy-reload.sh`.

## AI Working Notes
- Keep secrets in `.env` (`N8N_KEY`, `PSQL_PWD`, `REDIS_PWD`, SMTP, domain vars).
- Preserve shared env anchor `x-n8n-common-env` to keep master/worker parity.
- Do not remove queue-mode dependencies (`n8n-psql` and `n8n-redis` health checks).
