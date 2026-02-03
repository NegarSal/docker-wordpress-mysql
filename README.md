# Dockerized WordPress with MySQL

This project provides a production-ready WordPress environment using Docker Compose.
The stack includes WordPress and MySQL with persistent storage, service isolation, and health checks.

## Technologies Used
- Docker
- Docker Compose
- WordPress
- MySQL

## Architecture
- WordPress runs in its own container
- MySQL runs in a separate container
- Containers communicate over a dedicated Docker network
- Data is persisted using Docker volumes
- Health checks ensure services are running before dependent services start

## Prerequisites
- Docker
- Docker Compose

## How to Run
```bash
docker compose up -d
```
## Access WordPress at:
http://localhost:8080

## Configuration
- Environment variables are managed using a .env file
- MySQL credentials and WordPress DB config are stored in environment variables

## Persistence
- WordPress data is stored using Docker volumes
- MySQL data remains intact even after containers are stopped or removed

## Troubleshooting
- Check logs:
```bash
docker logs <container_name>
```
- Restart containers if needed:
```bash
docker compose restart
```

## What I Learned
- Designing multi-container applications using Docker Compose
- Managing service dependencies
- Using volumes for persistent data
- Applying DevOps best practices for local development environments
