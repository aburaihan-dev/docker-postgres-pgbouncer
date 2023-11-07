# Docker Compose Deployment for PostgreSQL and PgBouncer

This guide outlines the steps to deploy PostgreSQL and PgBouncer using Docker Compose while sharing environment values via an `.env` file. This setup provides a convenient way to manage your configuration securely.

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)
<!-- - [Contributing](../CONTRIBUTING.md) -->

## About <a name="about"></a>

This project is designed for Deploying PostgreSQL with PgBouncer using Docker.

## Getting Started <a name="getting_started"></a>

These instructions will help you set up and run the project on your local machine for development and testing. For deployment instructions, refer to [deployment](#deployment).

### Prerequisites

Before you begin, make sure you have the following installed on your system:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)


### Usage <a name="usage"></a>

Follow these steps to set up a development environment:

1. Clone the project repository to your local machine:

   ```sh
   git clone https://github.com/aburaihan-dev/docker-postgres-pgbouncer.git

   cd docker-postgres-pgbouncer

   cp .env.example .env
   ```
2. Create an `.env` file in the project directory with the following content. Replace placeholders with your own values:

   ```env
   # PostgreSQL settings
   POSTGRES_USER=youruser
   POSTGRES_PASSWORD=yourpassword
   POSTGRES_DB=yourdb

   # PgBouncer settings
   DB_USER=youruser
   DB_PASSWORD=yourpassword
   DB_NAME=yourdb
   POOL_MODE=session
   MAX_CLIENT_CONN=100
   DEFAULT_POOL_SIZE=20
   SERVER_IDLE_TIMEOUT=300

   # Set the PostgreSQL host (use the service name or 'localhost' if on the same host)
   DB_HOST=postgres
   ```
3. Update the PostgreSQL and PgBouncer configurations in the docker-compose.yaml file if needed. Make sure the .env variables match the services' environment variables.
4. Run the project:
   ```sh
    docker compose up -d && docker compose logs -f
   ```
5. The containers should now be up and running. You can access it at `localhost:6432`.
6. Feel free to customize the `.env` file to include specific configurations.


