---
layout: post
title: "Docker Fundamentals: Containerizing Your Applications"
date: 2024-10-01
author: "Mason"
tags: ["Docker", "DevOps", "Containers", "Deployment"]
---

Docker has revolutionized how we develop, deploy, and scale applications. In this post, I'll cover Docker fundamentals and show you how to containerize your applications.

## What is Docker?

Docker is a containerization platform that packages your entire application and its dependencies into a standardized unit called a **container**.

### Containers vs Virtual Machines

| Aspect | Containers | VMs |
|--------|-----------|-----|
| **Size** | MB | GB |
| **Startup** | Seconds | Minutes |
| **Isolation** | Process-level | Full OS isolation |
| **Performance** | Native | Slight overhead |

## Key Concepts

### Images
A blueprint for creating containers. Contains:
- Operating system layer
- Application code
- Dependencies and libraries
- Environment variables

### Containers
Running instances of an image. Isolated, lightweight, and portable.

### Dockerfile
A text file with instructions to build an image.

## Creating Your First Dockerfile

Here's a simple example for a Node.js application:

```dockerfile
# Use official Node.js runtime as a parent image
FROM node:18-alpine

# Set working directory in container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Expose port
EXPOSE 3000

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s --retries=3 \
  CMD node healthcheck.js

# Run application
CMD ["npm", "start"]
```

## Building and Running

### Build the image
```bash
docker build -t my-app:1.0 .
```

### Run a container
```bash
docker run -p 3000:3000 my-app:1.0
```

### Run in background
```bash
docker run -d -p 3000:3000 --name my-app-container my-app:1.0
```

## Docker Compose

For multi-container applications:

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgres://db:5432/myapp
    depends_on:
      - db
    restart: unless-stopped

  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=myapp
      - POSTGRES_PASSWORD=secret
    volumes:
      - postgres_data:/var/lib/postgresql/data
    restart: unless-stopped

volumes:
  postgres_data:
```

### Run with Docker Compose
```bash
docker-compose up -d
docker-compose down
```

## Docker Best Practices

### 1. Use Small Base Images
```dockerfile
# ✅ Good: ~150MB
FROM node:18-alpine

# ❌ Large: ~1GB
FROM node:18
```

### 2. Multi-stage Builds
```dockerfile
# Build stage
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production stage
FROM node:18-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY package*.json ./
RUN npm install --production
CMD ["npm", "start"]
```

### 3. Layer Caching
```dockerfile
# ✅ Frequently changing code at bottom
FROM node:18
WORKDIR /app
COPY package*.json ./       # Cached unless dependencies change
RUN npm install
COPY . .                     # Re-run if code changes
CMD ["npm", "start"]
```

### 4. Use .dockerignore
```
node_modules
npm-debug.log
.git
.gitignore
.DS_Store
.env
```

### 5. Non-root User
```dockerfile
FROM node:18-alpine
RUN addgroup -g 1001 -S nodejs
RUN adduser -S nodejs -u 1001
USER nodejs
```

### 6. Health Checks
```dockerfile
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD curl -f http://localhost:3000/health || exit 1
```

## Common Docker Commands

```bash
# Image commands
docker images                      # List images
docker build -t name:tag .        # Build image
docker rmi image-id               # Remove image
docker push repo/image:tag        # Push to registry

# Container commands
docker ps                          # List running containers
docker ps -a                       # List all containers
docker run -it image bash         # Run interactive container
docker exec container-id bash     # Execute command in container
docker logs container-id          # View container logs
docker stop container-id          # Stop container
docker rm container-id            # Remove container

# Network & Volume
docker network create mynet       # Create network
docker volume create myvolume     # Create volume
docker volume ls                  # List volumes
```

## Deploying Containers

### AWS ECS
Elastic Container Service - Managed container orchestration

```json
{
  "name": "my-app",
  "image": "my-repo/my-app:latest",
  "portMappings": [
    {
      "containerPort": 3000,
      "hostPort": 3000
    }
  ],
  "memory": 512
}
```

### Docker Swarm
Built-in orchestration:
```bash
docker swarm init
docker service create --name myapp -p 3000:3000 my-image:tag
```

### Kubernetes
Industrial-grade orchestration (covered in future posts!)

## Real-World Example

Here's a complete setup for a React + Node.js application:

**Dockerfile (Node.js Backend)**
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

**Dockerfile (React Frontend)**
```dockerfile
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

**docker-compose.yml**
```yaml
version: '3.8'
services:
  backend:
    build: ./backend
    ports:
      - "5000:5000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgres://db:5432/myapp

  frontend:
    build: ./frontend
    ports:
      - "80:80"
    depends_on:
      - backend

  db:
    image: postgres:15
    environment:
      - POSTGRES_PASSWORD=secret
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## Benefits of Docker

✅ **Consistency**: "It works on my machine" problem solved
✅ **Isolation**: Applications don't interfere with each other
✅ **Scalability**: Easy to run multiple instances
✅ **Efficiency**: Lightweight compared to VMs
✅ **Development**: Match production environment locally

## Conclusion

Docker simplifies deployment and makes applications more portable. Key takeaways:

1. Start with simple Dockerfiles
2. Use Docker Compose for multi-container apps
3. Follow best practices for efficiency
4. Test locally before deploying
5. Use registries like Docker Hub for distribution

Docker is an essential tool in modern development. Learning it will make you a more effective developer!

---

Have you used Docker in your projects? Share your experiences in the comments!
