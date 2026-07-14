# Dockerized WordPress with Nginx Reverse Proxy

This project demonstrates a multi-container WordPress application using Docker Compose.

The stack includes Nginx as a Reverse Proxy, WordPress, and MySQL with persistent storage, service isolation, and health checks.

## Technologies Used
- Docker
- Docker Compose
- Nginx
- WordPress
- MySQL
- GitHub Actions
- GitHub Secrets

## Architecture
- Nginx acts as a Reverse Proxy.
- WordPress runs in its own container.
- MySQL runs in a separate container.
- Containers communicate over a dedicated Docker network.
- Data is persisted using Docker volumes.
- Health checks monitor service availability.
- CI validation is performed using GitHub Actions.

## Architecture Diagram

```text
Browser
    │
    ▼
Nginx (Reverse Proxy)
    │
    ▼
WordPress
    │
    ▼
MySQL
``` 

## Prerequisites
- Docker
- Docker Compose

## How to Run

```bash
cp .env.example .env
docker compose up -d
```

## Access WordPress at:

```text
http://localhost:8080
```

## Configuration
- Environment variables are managed using a .env file 
- Create your `.env` file by copying `.env.example`.
- MySQL credentials and WordPress DB config are stored in environment variables

## Persistence
- WordPress data is stored using Docker volumes
- MySQL data remains intact even after containers are stopped or removed

## Troubleshooting
- Check logs:
```bash
docker compose logs
```
- Restart containers if needed:
```bash
docker compose restart
```

## What I Learned

- Designing multi-container applications using Docker Compose
- Managing service dependencies
- Using volumes for persistent data
- Configuring Nginx as a Reverse Proxy
- Managing application traffic through a reverse proxy
- Applying DevOps best practices for local development environments
- Building CI pipelines using GitHub Actions
- Managing sensitive configuration with GitHub Repository Secrets

## Continuous Integration

This project uses GitHub Actions to:

- Validate the Docker Compose configuration
- Start the application stack
- Verify service availability using an HTTP health check

Sensitive configuration is securely managed using GitHub Repository Secrets.
