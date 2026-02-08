# Docker Images & Docker History – Complete Guide

This README provides a **detailed explanation of Docker Images and Docker History**, including commands, examples, and best practices.  
It is suitable for **learning, interviews, documentation, and training material**.

---

## Table of Contents

1. Introduction to Docker Images
2. What is a Docker Image?
3. Docker Image Architecture
4. Docker Image Commands (Complete)
5. Docker Images with Examples
6. Docker Image Tagging & Versioning
7. Docker Image Layers
8. What is Docker History?
9. Docker History Command
10. Docker History with Examples
11. Practical Use Cases
12. Best Practices
13. Interview Notes
14. Summary

---

## 1. Introduction to Docker Images

A **Docker Image** is a **read-only template** used to create containers.  
Images contain application code, runtime, libraries, environment variables, and configuration files.

> Containers are running instances of Docker images.

---

## 2. What is a Docker Image?

- Immutable
- Layered
- Reusable
- Portable across environments

Example:
```bash
docker run nginx
```
Docker pulls the image (if not present) and creates a container.

---

## 3. Docker Image Architecture

```
Application Layer
-----------------
Runtime Layer
-----------------
OS Libraries
-----------------
Base Image (OS)
```

Each line represents an **image layer**.

---

## 4. Docker Image Commands (Complete)

### List Images
```bash
docker images
```

### Pull Image
```bash
docker pull nginx
```

### Remove Image
```bash
docker rmi nginx
```

### Remove Unused Images
```bash
docker image prune
```

### Inspect Image
```bash
docker image inspect nginx
```

---

## 5. Docker Images with Examples

### Pull an Image
```bash
docker pull ubuntu:22.04
```

### Run Image
```bash
docker run -it ubuntu:22.04 bash
```

### Build Image from Dockerfile
```bash
docker build -t myapp:1.0 .
```

---

## 6. Docker Image Tagging & Versioning

### Tag Image
```bash
docker tag myapp:1.0 myrepo/myapp:1.0
```

### Push Image
```bash
docker push myrepo/myapp:1.0
```

### Common Tags
- `latest`
- `1.0`
- `1.1`
- `stable`

---

## 7. Docker Image Layers

- Each instruction in Dockerfile creates a new layer
- Layers are cached
- Layers are shared between images

Example:
```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["npm","start"]
```

---

## 8. What is Docker History?

`docker history` shows the **layer-by-layer history** of an image, including:
- Image size
- Command used
- Layer creation order

---

## 9. Docker History Command

```bash
docker history IMAGE_NAME
```

Example:
```bash
docker history nginx
```

---

## 10. Docker History with Example

```bash
docker history ubuntu:22.04
```

Output shows:
- Each layer size
- Dockerfile instruction
- Build command

---

## 11. Practical Use Cases

- Identify large layers
- Optimize Dockerfile
- Debug image build issues
- Reduce image size

---

## 12. Best Practices

- Use small base images (alpine)
- Combine RUN commands
- Remove unnecessary files
- Use .dockerignore
- Tag images properly

---

## 13. Interview Notes

- Images are immutable
- Containers are runtime instances
- Docker history shows image layers
- Each Dockerfile instruction creates a layer

---

## 14. Summary

> Docker Images are the foundation of containers.  
> Docker History helps understand and optimize image layers.

---

## References

- Docker Official Documentation
- Docker CLI Reference
