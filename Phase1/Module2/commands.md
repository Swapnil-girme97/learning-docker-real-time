Docker Commands Cheat Sheet

Check Version

docker --version

---

Pull Image

docker pull nginx

---

List Images

docker images

---

Run Container

docker run nginx

---

Run Detached Container

docker run -d nginx

---

List Running Containers

docker ps

---

List All Containers

docker ps -a

---

Stop Container

docker stop <container-id>

---

Start Container

docker start <container-id>

---

Restart Container

docker restart <container-id>

---

Remove Container

docker rm <container-id>

---

Remove Image

docker rmi <image-name>