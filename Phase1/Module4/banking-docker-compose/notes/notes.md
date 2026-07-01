
# Docker Compose - Banking Application

## Project Overview

This project demonstrates how to deploy multiple web applications using Docker Compose.

Instead of manually running multiple Docker containers, Docker Compose allows us to define all containers inside a single YAML file and manage them using one command.

This project contains four independent banking services:

- Internet Banking
- Mobile Banking
- Insurance
- Loans

Each service is developed using HTML and CSS and hosted using Apache Web Server inside an Ubuntu Docker container.

---

# Project Structure

```
banking-docker-compose/

├── docker-compose.yaml

├── internet-banking/
│   ├── Dockerfile
│   ├── index.html
│   └── style.css

├── mobile-banking/
│   ├── Dockerfile
│   ├── index.html
│   └── style.css

├── insurance/
│   ├── Dockerfile
│   ├── index.html
│   └── style.css

└── loans/
    ├── Dockerfile
    ├── index.html
    └── style.css
```

---

# What is Docker Compose?

Docker Compose is a tool used to define and manage multiple Docker containers using a single YAML file.

Instead of executing multiple docker run commands manually, Docker Compose automates container creation, networking, and startup.

---

# Why Docker Compose?

Suppose we have four applications.

Internet Banking

Mobile Banking

Insurance

Loans

Without Docker Compose we need to execute:

docker run ...

docker run ...

docker run ...

docker run ...

every time.

Docker Compose solves this problem by allowing us to start all services using a single command.

```
docker compose up -d
```

---

# Docker Compose Workflow

Step 1

Create application files

```
index.html
style.css
```

↓

Step 2

Create Dockerfile for every application

↓

Step 3

Build Docker Images

↓

Step 4

Create docker-compose.yaml

↓

Step 5

Run all containers

```
docker compose up -d
```

↓

Step 6

Access applications from browser

---

# Dockerfile Explanation

Example:

```dockerfile
FROM ubuntu:22.04

RUN apt update -y

RUN apt install apache2 -y

COPY index.html /var/www/html/

COPY style.css /var/www/html/

EXPOSE 80

CMD ["/usr/sbin/apachectl","-D","FOREGROUND"]
```

## FROM

Downloads Ubuntu image.

```
FROM ubuntu:22.04
```

---

## RUN

Executes Linux commands while building the Docker image.

```
RUN apt update -y
```

updates package repository.

```
RUN apt install apache2 -y
```

installs Apache Web Server.

---

## COPY

Copies files from local machine into Docker image.

```
COPY index.html /var/www/html/
```

```
COPY style.css /var/www/html/
```

Apache serves files from:

```
/var/www/html/
```

---

## EXPOSE

Documents that the container listens on port 80.

```
EXPOSE 80
```

---

## CMD

Starts Apache when container starts.

```
CMD ["/usr/sbin/apachectl","-D","FOREGROUND"]
```

FOREGROUND keeps Apache running.

If Apache stops, container exits.

---

# docker-compose.yaml

Example

```yaml
services:

  internetbanking:
    image: internet-banking:v1
    ports:
      - "8081:80"

  mobilebanking:
    image: mobile-banking:v1
    ports:
      - "8082:80"

  insurance:
    image: insurance:v1
    ports:
      - "8083:80"

  loans:
    image: loans:v1
    ports:
      - "8084:80"
```

---

# Explanation

## services

Defines all containers.

Each application becomes one service.

---

## image

Docker image to run.

Example

```
image: internet-banking:v1
```

---

## ports

Maps host port to container port.

Example

```
8081:80
```

Meaning

Host Machine

```
8081
```

↓

Docker Container

```
80
```

Browser request

```
http://Public-IP:8081
```

↓

Docker

↓

Apache

↓

Website

---

# Commands

## Build Image

```
docker build -t internet-banking:v1 .
```

---

## Check Images

```
docker images
```

---

## Run All Services

```
docker compose up -d
```

---

## Stop Containers

```
docker compose stop
```

---

## Start Containers

```
docker compose start
```

---

## Restart Containers

```
docker compose restart
```

---

## Remove Containers

```
docker compose down
```

---

## View Running Containers

```
docker ps
```

---

## View Logs

```
docker compose logs
```

Specific service

```
docker compose logs internetbanking
```

---

## Rebuild Images

```
docker compose up --build
```

or

```
docker compose up -d --build
```

---

# Browser URLs

Internet Banking

```
http://Public-IP:8081
```

Mobile Banking

```
http://Public-IP:8082
```

Insurance

```
http://Public-IP:8083
```

Loans

```
http://Public-IP:8084
```

---

# Advantages of Docker Compose

- Single command deployment
- Easy container management
- Automatic network creation
- Easy scaling
- Less manual work
- Better project organization
- Easy for development and testing
- Faster deployment

---

# Limitations of Docker Compose

- Single host only
- No auto healing
- No automatic scaling
- No rolling updates
- No load balancing
- Not suitable for production clusters

These limitations are solved by Kubernetes.

---

# Interview Questions

### What is Docker Compose?

Docker Compose is a tool used to define and manage multiple Docker containers using one YAML configuration file.

---

### Why use Docker Compose?

To avoid running multiple docker run commands manually.

---

### What is docker-compose.yaml?

It is the configuration file that defines services, images, ports, networks, and volumes.

---

### Difference between Docker and Docker Compose?

Docker manages one container.

Docker Compose manages multiple containers.

---

### Which command starts all services?

```
docker compose up -d
```

---

### Which command stops all services?

```
docker compose down
```

---

### Why is Docker Compose useful?

It simplifies deployment of multi-container applications.

---

# Learning Outcome

After completing this project I learned:

- Docker Image creation
- Dockerfile
- Apache inside Docker
- Port Mapping
- Docker Compose
- Multi-container deployment
- Container Networking
- Docker Compose commands
- Managing multiple services using a single YAML file

Next Learning:

Docker Swarm → Kubernetes → Amazon ECR → Jenkins CI/CD → Amazon EKS → Monitoring