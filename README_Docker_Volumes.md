# Docker Volumes – Complete Reference Guide

This document is a comprehensive, end-to-end guide to Docker Volumes covering concepts, commands, examples, and best practices.

---

## Table of Contents
1. What is a Docker Volume
2. Why Docker Volumes are Needed
3. Types of Docker Storage
4. Docker Volume Architecture
5. Volume Lifecycle
6. Docker Volume Commands
7. Using Volumes with Containers
8. Named Volume vs Bind Mount
9. Anonymous Volumes
10. Database Example
11. Sharing Volumes
12. Read-Only Volumes
13. Volumes in Dockerfile
14. Volumes with Docker Compose
15. Backup and Restore
16. Best Practices
17. Interview Notes
18. Summary

---

## 1. What is a Docker Volume?
A Docker Volume is a Docker-managed storage mechanism used to persist data outside the container lifecycle.

---

## 2. Why Docker Volumes are Needed
- Containers are ephemeral
- Data is lost on container removal
- Volumes persist data across restarts

---

## 3. Types of Docker Storage
- Volumes (recommended)
- Bind mounts
- tmpfs mounts

---

## 4. Docker Volume Architecture
Container → Volume → Host File System

---

## 5. Volume Lifecycle
Create → Attach → Use → Container Removed → Data Persists

---

## 6. Docker Volume Commands

```bash
docker volume create my_volume
docker volume ls
docker volume inspect my_volume
docker volume rm my_volume
docker volume prune
```

---

## 7. Using Volumes with Containers

```bash
docker run -v my_volume:/data alpine
```

---

## 8. Named Volume vs Bind Mount

```bash
docker run -v my_volume:/data alpine
docker run -v /host/path:/data alpine
```

---

## 9. Anonymous Volumes

```bash
docker run -v /data nginx
```

---

## 10. Database Example (MySQL)

```bash
docker volume create mysql_data

docker run -d \
  --name mysql \
  -e MYSQL_ROOT_PASSWORD=1234 \
  -v mysql_data:/var/lib/mysql \
  mysql:8
```

---

## 11. Sharing Volumes

```bash
docker run -d -v shared:/data --name c1 alpine
docker run -d -v shared:/data --name c2 alpine
```

---

## 12. Read-Only Volumes

```bash
docker run -v my_volume:/data:ro alpine
```

---

## 13. Volumes in Dockerfile

```dockerfile
VOLUME /app/data
```

---

## 14. Volumes with Docker Compose

```yaml
version: "3.9"
services:
  app:
    image: nginx
    volumes:
      - web_data:/usr/share/nginx/html

volumes:
  web_data:
```

---

## 15. Backup and Restore

```bash
docker run --rm -v my_volume:/data -v $(pwd):/backup alpine tar czf /backup/backup.tar.gz /data
```

---

## 16. Best Practices
- Use named volumes
- Avoid bind mounts in production
- Backup regularly

---

## 17. Interview Notes
- Volumes persist after container deletion
- Stored in /var/lib/docker/volumes

---

## 18. Summary
Containers are stateless. Volumes make them stateful.
