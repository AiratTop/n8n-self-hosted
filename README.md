# n8n Self-Hosted with Docker

![n8n-self-hosted](https://repository-images.githubusercontent.com/1070157632/1698cbad-672c-43cf-99fe-27d89a8fdc22)

This repository provides a Docker Compose setup for running a self-hosted [n8n](https://n8n.io/) instance with scaling capabilities.

## Features

- **Works out of the box:** Just configure the `.env` file and run the start script.
- **Scalable:** Runs n8n in `queue` mode with separate workers, ready for high loads.
- **Handles Large Files:** Configured to save binary data to the filesystem, allowing workflows to process large files without memory issues.
- **Ready-to-use Scripts:** Includes simple scripts to start, restart, and update the application.
- **Long-term History:** Execution history is stored for 2 months.
- **Secure:** Uses the latest recommended security environment variables for n8n.
- **Private:** n8n telemetry is disabled by default.
- **Full-featured:** SMTP is pre-configured for password recovery and other email functions.
- **Automatic HTTPS:** Uses Caddy as a reverse proxy for automatic SSL certificates.
- **Persistent Data:** Data is stored in a PostgreSQL database.
- **Caching:** Uses Redis for caching.

## Prerequisites

- Docker and Docker Compose installed.
- A domain name pointed to your server's IP address.
- A `.env` file with the required environment variables.

## Usage

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/AiratTop/n8n-self-hosted
    cd n8n-self-hosted
    ```

2.  **Create the shared network:**
    This setup uses a shared network to easily connect to external databases. If you haven't already, create the network:
    ```bash
    docker network create shared_network
    ```

3.  **Configure the environment:**
    Open the `.env` file and update the variables with your own settings.

4.  **Start the application:**
    ```bash
    ./start-docker.sh
    ```
    This will start all the services in detached mode and scale the `n8n-worker` service to 2 replicas.

5.  **Restart the application:**
    ```bash
    ./restart-docker.sh
    ```

6.  **Update the application:**
    ```bash
    ./update-docker.sh
    ```
    This will automatically create a database backup, pull the latest Docker images, and restart the application.

## Backup

This project includes a script to back up the n8n database.

To create a backup, run:
```bash
./backup.sh
```
This will create a compressed SQL dump of your PostgreSQL database in the `local_files/backups/` directory. It is recommended to run this script regularly (e.g., using a cron job).

## Connecting to Other Services

This n8n setup is part of a larger ecosystem of self-hosted services that can all run on the same `shared_network`. This allows n8n to securely connect to them using their container names as hostnames.

## See Also

Check out these pre-configured services that work out-of-the-box with this n8n instance:

-   [**postgresql-self-hosted**](https://github.com/AiratTop/postgresql-self-hosted): A simple and robust PostgreSQL setup.
-   [**mysql-self-hosted**](https://github.com/AiratTop/mysql-self-hosted): A self-hosted MySQL instance.
-   [**clickhouse-self-hosted**](https://github.com/AiratTop/clickhouse-self-hosted): High-performance columnar database for analytics.
-   [**metabase-self-hosted**](https://github.com/AiratTop/metabase-self-hosted): Self-hosted Metabase on Docker for business intelligence and analytics.
-   [**qdrant-self-hosted**](https://github.com/AiratTop/qdrant-self-hosted): A vector database for AI applications.
-   [**redis-self-hosted**](https://github.com/AiratTop/redis-self-hosted): A fast in-memory data store, often used as a cache or message broker.
-   [**caddy-self-hosted**](https://github.com/AiratTop/caddy-self-hosted): A modern, easy-to-use web server with automatic HTTPS.
-   [**wordpress-self-hosted**](https://github.com/AiratTop/wordpress-self-hosted): Production-ready WordPress stack with MySQL, phpMyAdmin, and WP-CLI.
-   [**n8n-self-hosted**](https://github.com/AiratTop/n8n-self-hosted): Scalable n8n with workers, Caddy for auto-HTTPS, and backup scripts.
-   [**monitoring-self-hosted**](https://github.com/AiratTop/monitoring-self-hosted): Self-hosted monitoring stack with Prometheus and Grafana.
-   [**ollama-self-hosted**](https://github.com/AiratTop/ollama-self-hosted): Ready-to-use solution for running Ollama with the Open WebUI on Docker.
-   [**authentik-self-hosted**](https://github.com/AiratTop/authentik-self-hosted): Authentik is a flexible, open-source Identity & Access Management (IAM) solution.
-   [**gatus-self-hosted**](https://github.com/AiratTop/gatus-self-hosted): Automated service health dashboard with a PostgreSQL backend and backup scripts.
-   [**beszel-self-hosted**](https://github.com/AiratTop/beszel-self-hosted): Ready-to-run Beszel hub + agent stack for monitoring your infrastructure.

## Services

- `caddy`: Reverse proxy
- `n8n-master`: Main n8n instance
- `n8n-worker`: n8n worker instances
- `n8n-psql`: PostgreSQL database
- `n8n-redis`: Redis cache

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Author

**AiratTop**

- Website: [airat.top](https://airat.top)
- GitHub: [@AiratTop](https://github.com/AiratTop)
- Email: [mail@airat.top](mailto:mail@airat.top)
- Repository: [n8n-self-hosted](https://github.com/AiratTop/n8n-self-hosted)
