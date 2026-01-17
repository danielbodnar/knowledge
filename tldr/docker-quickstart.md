# Quick Start: Docker

> Get started with Docker in 5 minutes

## What is Docker?

Docker is a platform for developing, shipping, and running applications in containers.

## Prerequisites

- Operating System: Windows 10/11, macOS, or Linux
- 4GB RAM minimum
- Administrative/sudo access

## Installation

### macOS
```bash
brew install --cask docker
```

### Linux (Ubuntu/Debian)
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### Windows
Download Docker Desktop from https://www.docker.com/products/docker-desktop

## Verify Installation

```bash
docker --version
docker run hello-world
```

## Basic Usage

### Run a Container

```bash
# Run nginx web server
docker run -d -p 8080:80 nginx

# Visit http://localhost:8080
```

### List Containers

```bash
# Running containers
docker ps

# All containers
docker ps -a
```

### Stop Container

```bash
docker stop container-id
```

## Create Your First Dockerfile

Create `Dockerfile`:

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

Build and run:

```bash
docker build -t myapp .
docker run -p 3000:3000 myapp
```

## Common Commands

```bash
# Build image
docker build -t name:tag .

# Run container
docker run -d -p host:container image

# View logs
docker logs container-id

# Execute command
docker exec -it container-id sh

# Stop all containers
docker stop $(docker ps -q)

# Remove all containers
docker rm $(docker ps -aq)
```

## Next Steps

- Learn about Docker Compose for multi-container apps
- Explore Docker Hub for pre-built images
- Study Dockerfile best practices
- Try Docker volumes for persistent data

## Resources

- [Docker Documentation](https://docs.docker.com)
- [Docker Getting Started Tutorial](https://docs.docker.com/get-started/)
- [Docker Cheatsheet](../cheatsheets/docker-cheatsheet.md)
