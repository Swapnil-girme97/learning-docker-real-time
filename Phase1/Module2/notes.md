Module 2 - Docker Installation & Commands

Docker Engine

Docker Engine is the runtime environment responsible for building and running containers.

Components

- Docker Client
- Docker Daemon
- REST API

---

Docker Client

Used to execute Docker commands.

Examples:

docker build
docker run
docker ps
docker images

---

Docker Daemon

Background service responsible for:

- Images
- Containers
- Networks
- Volumes

---

Verify Docker Installation

docker run hello-world

Workflow:

Docker Client
↓
Docker Daemon
↓
Pull hello-world Image
↓
Create Container
↓
Execute Container

---

Docker Images

Images are read-only templates used to create containers.

Examples:

- nginx
- ubuntu
- mysql
- redis

---

Docker Containers

A container is a running instance of an image.

Image
↓
Container

---

Docker Lifecycle

Pull Image
↓
Run Container
↓
Manage Container
↓
Stop Container
↓
Remove Container

---

Key Takeaways

- Images are templates.
- Containers are running instances.
- Docker Engine manages the container lifecycle.
- Docker commands are used through Docker Client.
