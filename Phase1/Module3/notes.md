
# Docker Notes.md

# 🐳 Docker Images & Containers - DevOps Notes

---

# 1. Docker Images

## What is a Docker Image?

A Docker Image is a **read-only blueprint** used to create containers.

Think of it like:

* Image = Class
* Container = Object

Examples:

```bash
nginx
ubuntu
mysql
mongo
redis
node
```

---

## Pull Image

```bash
docker pull nginx
docker pull ubuntu
docker pull mysql:8
```

---

## List Images

```bash
docker images
```

or

```bash
docker image ls
```

Output

```
REPOSITORY   TAG       IMAGE ID      SIZE

ubuntu       latest    4dd97cefde62  77MB

nginx        latest    605c77e624dd  142MB
```

---

## Remove Image

```bash
docker rmi nginx
```

Remove by Image ID

```bash
docker rmi IMAGE_ID
```

Force delete

```bash
docker rmi -f IMAGE_ID
```

Delete all images

```bash
docker rmi $(docker images -q)
```

---

# 2. Docker Containers

A Container is a **running instance of an Image**.

```
Image
   ↓
Container
```

Example

```bash
docker run nginx
```

Docker first checks

* Image exists?
* If No → Pull image
* Create container
* Start container

---

# Run Container

Interactive Ubuntu

```bash
docker run -it ubuntu
```

Detached Mode

```bash
docker run -d nginx
```

Name the container

```bash
docker run -d --name web nginx
```

Port Mapping

```bash
docker run -d -p 80:80 nginx
```

---

# List Containers

Running containers

```bash
docker ps
```

All containers

```bash
docker ps -a
```

---

# Stop Container

```bash
docker stop container_name
```

Example

```bash
docker stop web
```

---

# Start Container

```bash
docker start web
```

---

# Restart Container

```bash
docker restart web
```

---

# Pause Container

Pauses all processes inside the container.

```bash
docker pause web
```

Check

```bash
docker ps
```

STATUS

```
Paused
```

---

# Unpause Container

```bash
docker unpause web
```

---

# Kill Container

Immediately stops container.

```bash
docker kill web
```

Difference

```
docker stop
↓

Gracefully stops container

docker kill
↓

Immediately terminates container
```

---

# Delete Container

Container must be stopped first.

```bash
docker rm web
```

Force delete

```bash
docker rm -f web
```

Delete all stopped containers

```bash
docker container prune
```

Delete all containers

```bash
docker rm -f $(docker ps -aq)
```

---

# Delete Images

Single Image

```bash
docker rmi ubuntu
```

By Image ID

```bash
docker rmi IMAGE_ID
```

All Images

```bash
docker rmi $(docker images -q)
```

Force Delete

```bash
docker rmi -f IMAGE_ID
```

---

# Docker Prune Commands

## Remove stopped containers

```bash
docker container prune
```

---

## Remove unused images

```bash
docker image prune
```

---

## Remove unused networks

```bash
docker network prune
```

---

## Remove unused volumes

```bash
docker volume prune
```

---

## Remove EVERYTHING unused

```bash
docker system prune
```

More aggressive

```bash
docker system prune -a
```

Also remove volumes

```bash
docker system prune -a --volumes
```

---

# Docker Image Backup

Create backup

```bash
docker save -o ubuntu.tar ubuntu
```

or

```bash
docker save ubuntu > ubuntu.tar
```

Check

```bash
ls
```

Output

```
ubuntu.tar
```

---

# Restore Image

```bash
docker load -i ubuntu.tar
```

or

```bash
docker load < ubuntu.tar
```

Verify

```bash
docker images
```

---

# Export Running Container

Save filesystem only

```bash
docker export container_name > app.tar
```

Restore

```bash
cat app.tar | docker import - app:v1
```

Difference

```
save/load
↓

Complete Image

export/import
↓

Only Container Filesystem
```

---

# Docker Attach vs Docker Exec

## docker attach

Attaches to the **main running process**.

```bash
docker attach container_name
```

Example

```bash
docker attach ubuntu
```

Exit without stopping

```
CTRL + P
CTRL + Q
```

Typing

```
exit
```

stops the container.

---

## docker exec

Starts a **new process** inside an already running container.

```bash
docker exec -it container_name bash
```

Example

```bash
docker exec -it web bash
```

Exit

```bash
exit
```

Container keeps running.

---

### Comparison

| docker attach            | docker exec                      |
| ------------------------ | -------------------------------- |
| Connects to main process | Starts new process               |
| exit may stop container  | exit does not stop container     |
| Less commonly used       | Most commonly used in production |
| No new shell             | Opens a new shell                |

---

# Difference Between -it and -d

## -i

Interactive mode

Keeps STDIN open.

---

## -t

Allocates a terminal.

---

Together

```bash
-it
```

Example

```bash
docker run -it ubuntu
```

You get

```
root@container:/#
```

Useful for

* Ubuntu
* Alpine
* CentOS
* Troubleshooting

---

## -d

Detached Mode

Runs in background.

```bash
docker run -d nginx
```

Returns

```
Container ID
```

Container runs in background.

---

## -itd

Interactive + TTY + Detached

```bash
docker run -itd ubuntu
```

Container runs in background while keeping an interactive terminal available later.

Later connect

```bash
docker exec -it container_name bash
```

or

```bash
docker attach container_name
```

---

# Common Docker Commands

```bash
docker images
docker ps
docker ps -a
docker pull ubuntu
docker run -it ubuntu
docker run -d nginx
docker stop container
docker start container
docker restart container
docker pause container
docker unpause container
docker kill container
docker rm container
docker rm -f container
docker rmi image
docker image prune
docker container prune
docker system prune -a
docker save -o ubuntu.tar ubuntu
docker load -i ubuntu.tar
docker exec -it container bash
docker attach container
docker logs container
docker inspect container
docker stats
docker top container
docker history ubuntu
docker version
docker info
```

---

# Interview Tips

✅ Image = Blueprint

✅ Container = Running Instance

✅ `docker exec -it` is preferred over `docker attach` in production.

✅ `docker stop` sends SIGTERM then SIGKILL after a timeout, while `docker kill` sends SIGKILL immediately (unless another signal is specified).

✅ `docker save/load` preserves image layers and tags.

✅ `docker export/import` only preserves the container filesystem and loses image history and metadata.

✅ `docker system prune -a --volumes` removes all unused containers, images, networks, and volumes—use with caution.
