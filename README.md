# Wagtail PGVector Template
Template repository with Wagtail CMS and Postgres and pg_vector extension devcontainer configuration

## Description
This repository provides a template for setting up a development environment with Wagtail CMS, PostgreSQL, and pgvector extension support. The configuration is designed to work with Visual Studio Code Dev Containers.

## Features
- Wagtail CMS
- PostgreSQL with pgvector extension
- Devcontainer configuration for easy setup

## Getting Started
To get started with this template, follow the steps below:

1. Clone the repository:
   ```sh
   git clone https://github.com/brylie/wagtail-pgvector-template.git
   cd wagtail-pgvector-template
   ```

2. Open the repository in Visual Studio Code:
   ```sh
   code .
   ```

3. When prompted, open the repository in a devcontainer.

## Configuration
The devcontainer is configured to use the `pgvector/pgvector` image for the PostgreSQL service. This ensures that the pgvector extension is available for vector operations.

### Docker Compose Configuration
The `docker-compose.yml` file in the `.devcontainer` directory specifies the services and their configurations.

### pgAdmin4 Integration
The devcontainer now includes a service definition for `pgAdmin4` to facilitate easier management and interaction with the PostgreSQL database instance. The `pgAdmin4` service is configured in the `docker-compose.yml` file and can be accessed via a web interface.

## Accessing pgAdmin4
To access pgAdmin4 in the DevContainer environment, follow these steps:

1. Ensure the DevContainer is running.
2. Open a web browser and navigate to `http://localhost:5050`.
3. Log in with the default credentials:
   - **Email**: `admin@admin.com`
   - **Password**: `admin`
4. Once logged in, you can manage and interact with the PostgreSQL database instance.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
