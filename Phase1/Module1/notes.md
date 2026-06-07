
Module 1 - Docker Fundamentals

What is Docker?

Docker is an open-source containerization platform used to package applications and their dependencies into lightweight containers.

Docker ensures applications run consistently across development, testing, and production environments.

Docker Motto

Build Once, Run Anywhere.

---

Why Docker Was Introduced

Before Docker, developers often faced environment-related issues.

Example:

Developer Machine:

- Java 17
- Ubuntu 22.04

Production Server:

- Java 11
- Ubuntu 18.04

Application works locally but fails in production.

This is known as:

"It works on my machine" problem.

Docker solves this problem by packaging:

- Application code
- Runtime
- Libraries
- Dependencies
- Configuration

inside a container.

---

What is a Container?

A container is an isolated environment that contains everything required to run an application.

Characteristics:

- Lightweight
- Portable
- Fast Startup
- Resource Efficient

---

Virtual Machine vs Container

Virtual Machine

- Includes full Guest OS
- Higher resource consumption
- Slow startup

Container

- Shares host OS kernel
- Lightweight
- Starts within seconds

---

Docker Architecture

Docker consists of:

Docker Client

Used to execute Docker commands.

Examples:

docker build

docker run

docker ps

---

Docker Daemon

Background service responsible for:

- Building images
- Running containers
- Managing networks
- Managing volumes

---

Docker Registry

Stores Docker images.

Examples:

- Docker Hub
- AWS ECR

---

Docker Lifecycle

Dockerfile
↓
Docker Image
↓
Docker Container

---

Docker in DevOps

Developer
↓
GitHub
↓
Jenkins
↓
Docker Build
↓
Docker Registry
↓
Kubernetes
↓
Production

---

Benefits of Docker

- Environment Consistency
- Faster Deployment
- Scalability
- Portability
- Resource Efficiency
- Easy Rollback

---

Key Takeaways

- Docker is a containerization platform.
- Containers are lightweight and portable.
- Docker solves environment consistency issues.
- Images are templates used to create containers.
- Containers are running instances of images.