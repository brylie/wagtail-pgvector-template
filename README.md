# wagtail-pgvector-template
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
The devcontainer is configured to use the `pgvector/pgvector:latest` image for the PostgreSQL service. This ensures that the pgvector extension is available for vector operations.

### Docker Compose Configuration
The `docker-compose.yml` file in the `.devcontainer` directory specifies the services and their configurations.

Example configuration:
```yaml
services:
  app:
    build:
      context: ..
      dockerfile: .devcontainer/Dockerfile

    volumes:
      - ../..:/workspaces:cached

    command: sleep infinity

    network_mode: service:db

  db:
    image: pgvector/pgvector:latest
    restart: unless-stopped
    volumes:
      - postgres-data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: postgres
      POSTGRES_DB: postgres
      POSTGRES_PASSWORD: postgres

volumes:
  postgres-data:
```

## Custom Dockerfile for PostgreSQL (if needed)
If using the `pgvector/pgvector` image is not feasible, you can create a custom Dockerfile for the PostgreSQL service.

Example Dockerfile:
```dockerfile
# Use the official PostgreSQL image as the base
FROM postgres:latest

# Install pgvector extension
RUN apt-get update && apt-get install -y \
    postgresql-server-dev-all \
    && git clone https://github.com/pgvector/pgvector.git \
    && cd pgvector && make && make install \
    && rm -rf /var/lib/apt/lists/*

# Set the default command to run PostgreSQL
CMD ["postgres"]
```

Update `docker-compose.yml` to use the custom Dockerfile:
```yaml
services:
  db:
    build:
      context: .
      dockerfile: Dockerfile.postgres
    restart: unless-stopped
    volumes:
      - postgres-data:/var/lib/postgresql/data
    environment:
      POSTGRES_USER: postgres
      POSTGRES_DB: postgres
      POSTGRES_PASSWORD: postgres
```

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
