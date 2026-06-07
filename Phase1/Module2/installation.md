
Docker Installation Guide

Environment

- AWS EC2 Ubuntu Server
- Docker Engine

---

Update Packages

sudo apt update

---

Install Docker

sudo apt install docker.io -y

---

Start Docker Service

sudo systemctl start docker

---

Enable Docker Service

sudo systemctl enable docker

---

Verify Installation

docker --version

Example Output:

Docker version 28.x.x

---

Check Docker Status

sudo systemctl status docker

Expected:

active (running)

---

Run Test Container

docker run hello-world

This confirms Docker is working successfully.