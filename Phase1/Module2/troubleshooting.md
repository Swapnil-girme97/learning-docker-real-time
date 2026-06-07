
Docker Troubleshooting Guide

Error

Cannot connect to Docker daemon

Solution

sudo systemctl start docker

---

Error

permission denied while trying to connect to Docker daemon socket

Solution

sudo usermod -aG docker $USER
newgrp docker

---

Error

Container exited immediately

Solution

Check logs:

docker logs <container-id>

---

Verify Docker Service

sudo systemctl status docker

Expected:

active (running)