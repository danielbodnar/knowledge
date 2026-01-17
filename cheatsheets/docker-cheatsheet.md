---
title: "Docker Cheatsheet"
topic: "Docker"
category: "DevOps"
tags: [docker, containers, cheatsheet, cli, reference]
date_created: "2026-01-17"
last_updated: "2026-01-17"
---

# Docker Cheatsheet

## Quick Reference

Essential Docker commands for everyday use.

### Common Commands

```bash
# Build an image
docker build -t myimage:tag .

# Run a container
docker run -d -p 8080:80 --name mycontainer myimage:tag

# List containers
docker ps -a

# Stop a container
docker stop mycontainer

# Remove a container
docker rm mycontainer
```

## Container Management

| Command | Description | Example |
|---------|-------------|---------|
| `docker run` | Create and start a container | `docker run -it ubuntu bash` |
| `docker start` | Start a stopped container | `docker start mycontainer` |
| `docker stop` | Stop a running container | `docker stop mycontainer` |
| `docker restart` | Restart a container | `docker restart mycontainer` |
| `docker rm` | Remove a container | `docker rm mycontainer` |
| `docker ps` | List running containers | `docker ps` |
| `docker ps -a` | List all containers | `docker ps -a` |
| `docker logs` | View container logs | `docker logs mycontainer` |
| `docker exec` | Execute command in container | `docker exec -it mycontainer bash` |

## Image Management

| Command | Description | Example |
|---------|-------------|---------|
| `docker build` | Build image from Dockerfile | `docker build -t myimage .` |
| `docker pull` | Pull image from registry | `docker pull nginx:latest` |
| `docker push` | Push image to registry | `docker push myimage:tag` |
| `docker images` | List images | `docker images` |
| `docker rmi` | Remove an image | `docker rmi myimage:tag` |
| `docker tag` | Tag an image | `docker tag myimage:latest myimage:v1.0` |

## Docker Compose

| Command | Description | Example |
|---------|-------------|---------|
| `docker-compose up` | Start services | `docker-compose up -d` |
| `docker-compose down` | Stop services | `docker-compose down` |
| `docker-compose ps` | List services | `docker-compose ps` |
| `docker-compose logs` | View logs | `docker-compose logs -f` |
| `docker-compose build` | Build services | `docker-compose build` |

## Networking

```bash
# Create a network
docker network create mynetwork

# List networks
docker network ls

# Connect container to network
docker network connect mynetwork mycontainer

# Inspect network
docker network inspect mynetwork
```

## Volumes

```bash
# Create a volume
docker volume create myvolume

# List volumes
docker volume ls

# Mount volume to container
docker run -v myvolume:/data myimage

# Remove volume
docker volume rm myvolume
```

## Tips & Tricks

- Use `.dockerignore` to exclude files from build context
- Multi-stage builds reduce image size
- Use specific image tags, avoid `latest` in production
- Clean up unused resources: `docker system prune -a`
- Use `docker-compose` for multi-container applications
- Pin base image versions for reproducibility

## Common Patterns

```bash
# Clean up everything
docker system prune -a --volumes

# View container resource usage
docker stats

# Copy files from/to container
docker cp mycontainer:/path/to/file ./local/path
docker cp ./local/file mycontainer:/path/to/file

# Follow logs in real-time
docker logs -f mycontainer

# Run ephemeral container (auto-remove after exit)
docker run --rm -it ubuntu bash
```

## Dockerfile Best Practices

```dockerfile
# Use specific base image version
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Copy package files first (leverage cache)
COPY package*.json ./

# Install dependencies
RUN npm ci --only=production

# Copy application code
COPY . .

# Use non-root user
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001
USER nodejs

# Expose port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD node healthcheck.js

# Start application
CMD ["node", "server.js"]
```

## Resources

- [Official Docker Documentation](https://docs.docker.com)
- [Docker Hub](https://hub.docker.com)
- [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
