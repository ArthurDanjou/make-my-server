# make-my-server

🚀 A comprehensive Infrastructure as Code (IaC) repository for deploying and managing self-hosted services using Docker Compose.

## Overview

This repository contains Docker Compose configurations for a variety of self-hosted services that can be easily deployed to your server infrastructure. Each service is isolated in its own directory with proper configuration.

## Features

- 🔒 Secure reverse proxy with Traefik v3
- 🔍 Monitoring with Grafana and Prometheus
- 🔄 Container management with Portainer
- 📊 Database visualization with NocoDB
- 🧩 Workflow automation with n8n
- 🌐 DNS ad-blocking with AdGuard
- 🔎 Search engine with Meilisearch
- 🎮 Minecraft server
- ⏱️ Uptime monitoring with Uptime Kuma
- 📈 Speed testing with MySpeed
- ...and more!

## Prerequisites

- Docker and Docker Compose installed on your server
- Domain name with DNS pointing to your server
- Basic understanding of Docker and networking

## Directory Structure

Each service has its own directory containing at minimum a `docker-compose.yml` file:

```
make-my-server/
├── adguard/              # AdGuard Home DNS ad-blocker
├── data/                 # Persistent data storage
├── grafana/              # Monitoring dashboards
│   └── prometheus/       # Metrics collection
├── meilisearch/          # Search engine service
├── minecraft/            # Minecraft server
├── myspeed/              # Speed testing tool
├── n8n/                  # Workflow automation platform
├── nocodb/               # Database visualization
├── portainer/            # Container management UI
├── traefik/              # Reverse proxy and SSL termination
│   └── dynamics/         # Dynamic configuration files
└── uptime-kuma/          # Uptime monitoring
```

## Deployment

Each service can be deployed independently using Docker Compose:

```bash
# Navigate to the service directory
cd service-name

# Start the service
docker-compose up -d
```

For a complete deployment of all services:

```bash
# Clone the repository
git clone https://github.com/arthurdanjou/make-my-server.git
cd make-my-server

# Deploy Traefik first (recommended)
cd traefik
docker-compose up -d

# Then deploy other services as needed
cd ../service-name
docker-compose up -d
```

## Network Configuration

Services are configured to work with Traefik as a reverse proxy. Most services expose a web interface through Traefik with automatic HTTPS using Let's Encrypt.

## Data Persistence

All service data is persisted through Docker volumes, generally mapped to the `./data` directory or service-specific volumes.

## Security Considerations

- SSL certificates are automatically managed by Traefik
- Cloudflare integration is available for DNS challenges
- Environment variables are used for sensitive configuration

## Customization

Each service can be customized by modifying its `docker-compose.yml` file and any associated configuration files.

## License

This project is open source and available under the [MIT License](LICENSE).

## Author

Created and maintained by [Arthur Danjou](https://github.com/arthurdanjou).
