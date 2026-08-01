# Dockerized WordPress with Nginx Reverse Proxy

This project demonstrates a multi-container WordPress application using Docker Compose and Kubernetes.

The project includes Nginx as a Reverse Proxy, WordPress, MySQL, persistent storage, health checks, GitHub Actions, and Kubernetes manifests for local development with Kind.

## Technologies Used
- Docker
- Docker Compose
- Kubernetes (Kind)
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

## Kubernetes Deployment

This repository also contains a Kubernetes version of the application inside the `k8s/` directory.

Included resources:

- Namespace
- ConfigMap
- Secret
- PersistentVolume (PV)
- PersistentVolumeClaim (PVC)
- Deployment
- Service
- Ingress
- NGINX Ingress Controller

The Kubernetes deployment was tested locally using **Kind**.

> Note:
> The included `ingress-nginx.yaml` uses a mirror registry because the official Kubernetes registry may be inaccessible in some regions.

## Prerequisites
- Docker
- Docker Compose
- Kind
- kubectl

## How to Run

```bash
cp .env.example .env
docker compose up -d
```

## Access

### Docker Compose

```text
http://localhost:8080
```

### Kubernetes

After deploying the Kubernetes manifests and configuring the local host entry:

```text
http://wordpress.local
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

## Project Structure

```text
.
├── docker-compose.yml
├── nginx/
│   └── default.conf
├── k8s/
│   ├── namespace.yaml
│   ├── configmap.yaml
│   ├── secret.yaml
│   ├── pv.yaml
│   ├── pvc.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── ingress-nginx.yaml
│   └── kind-config.yaml
└── README.md
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
- Deploying applications on Kubernetes
- Managing Kubernetes networking using Services and Ingress
- Running Kubernetes locally with Kind

## Continuous Integration

This project uses GitHub Actions to:

- Validate the Docker Compose configuration
- Start the application stack
- Verify service availability using an HTTP health check

Sensitive configuration is securely managed using GitHub Repository Secrets.
