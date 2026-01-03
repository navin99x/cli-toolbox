# Docker — Container Platform

> 🐳 Platform for developing, shipping, and running applications in lightweight containers.

---

## Installation

Follow the [Docker installation guide](https://docs.docker.com/get-docker/) for your platform.

**Verify installation:**
```bash
docker --version
```

---

## Image Management

```bash
# Pull an image from registry
docker pull hello-world

# List local images
docker images

# Search for images in Docker Hub
docker search nginx

# Remove an image
docker rmi hello-world

# Remove unused images
docker image prune
```

---

## Container Management

### Basic Operations
```bash
# Run container from image
docker run hello-world

# Run with custom name
docker run --name my-app nginx

# Run in background (detached)
docker run -d nginx

# Run in interactive mode with terminal
docker run -it ubuntu bash
```

### Container Lifecycle
```bash
# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# Start/stop/restart existing container
docker start my-app
docker stop my-app
docker restart my-app

# Remove container
docker rm my-app

# Remove all stopped containers
docker container prune
```

### Container Interaction
```bash
# Execute command in running container
docker exec -it my-app bash

# View container logs
docker logs my-app

# Follow logs in real-time
docker logs -f my-app

# View container resource usage
docker stats my-app
```

---

## 🔗 Port Mapping

```bash
# Map host port to container port
docker run -d -p 8080:80 nginx
```

---

## Volume Management

### Named Volumes
```bash
# Create a volume
docker volume create my-vol

# Use volume in container
docker run -d -v my-vol:/data nginx

# List volumes
docker volume ls

# Inspect volume details
docker volume inspect my-vol

# Remove volume
docker volume rm my-vol

# Remove unused volumes
docker volume prune
```

### Bind Mounts
```bash
# Mount host directory to container
docker run -d -v /host/path:/container/path nginx

# Mount current directory
docker run -d -v $(pwd):/app nginx
```

---

## Network Management

```bash
# List networks
docker network ls

# Create custom network
docker network create my-network

# Run container on specific network
docker run -d --network my-network nginx

# Connect running container to network
docker network connect my-network my-app

# Disconnect container from network
docker network disconnect my-network my-app

# Remove network
docker network rm my-network
```

---

## Docker Compose

### Basic Commands
```bash
# Start services (foreground)
docker compose up

# Start services (background)
docker compose up -d

# Start specific service
docker compose up nginx

# Stop services
docker compose stop

# Stop and remove containers, networks, volumes
docker compose down
```

### Service Management
```bash
# List running services
docker compose ps

# View service logs
docker compose logs nginx

# Execute command in service container
docker compose exec nginx bash
```

---

## Sample docker-compose.yml

```yaml
version: '3.8'

services:
  db:
    image: postgres:15
    restart: always
    environment:
      POSTGRES_DB: myapp
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  web:
    image: nginx:alpine
    restart: always
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    depends_on:
      - db

  adminer:
    image: adminer:4
    restart: always
    ports:
      - "8081:8080"
    depends_on:
      - db

volumes:
  postgres_data:

networks:
  default:
    name: myapp-network
```

---

## 🧹 Cleanup Commands

```bash
# Remove all stopped containers, unused networks, images, and build cache
docker system prune

# Remove everything including unused volumes
docker system prune --volumes

# Remove all containers (including running)
docker rm -f $(docker ps -aq)

# Remove all images
docker rmi $(docker images -q)
```