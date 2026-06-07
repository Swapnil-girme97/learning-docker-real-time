Docker Architecture

Components

Docker Client

User interface used to communicate with Docker.

Examples:

docker build
docker run
docker ps

---

Docker Daemon

Background service responsible for:

- Image Management
- Container Management
- Networking
- Storage

---

Docker Registry

Stores Docker images.

Examples:

- Docker Hub
- Amazon ECR

---

Docker Architecture Diagram

"Docker Architecture" (./screenshots/docker-architecture.png)

---

Architecture Flow

Docker Client
      ↓
Docker Daemon
      ↓
Docker Registry
      ↓
Docker Image
      ↓
Docker Container

---

Docker Lifecycle Diagram

"Docker Lifecycle" (./screenshots/docker-lifecycle.png)

---

Docker Lifecycle

Dockerfile
      ↓
Docker Image
      ↓
Docker Container

---

VM vs Container Diagram

"VM vs Container" (./screenshots/vm-vs-container.png)

---

VM vs Container Comparison

Feature| Virtual Machine| Container
OS| Separate Guest OS| Shares Host OS
Startup Time| Minutes| Seconds
Resource Usage| High| Low
Performance| Lower| Higher
Size| GBs| MBs

---

Real-Time DevOps Flow

Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Docker Build
    ↓
Docker Hub / AWS ECR
    ↓
Kubernetes
    ↓
Production

Key Takeaways

- Docker Client communicates with Docker Daemon.
- Docker Daemon manages images, containers, networks, and volumes.
- Docker Registry stores Docker images.
- Containers are created from Docker Images.
- Docker is a key component in modern DevOps CI/CD pipelines.