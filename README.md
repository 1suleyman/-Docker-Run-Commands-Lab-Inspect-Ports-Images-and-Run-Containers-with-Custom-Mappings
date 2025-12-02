# 🐳 Docker Run Commands Lab — Inspect Ports, Images, and Run Containers with Custom Mappings

In this lab, I learned how to **inspect running containers, identify container images, check published ports, and run a new container with custom port mappings and a custom name**.

---

## 📋 Lab Overview

**Goal:**

* Inspect running containers
* Determine which image a container uses
* Check container-side vs host-side port mappings
* Run a new container using `docker run`
* Use custom port mappings and container names

**Learning Outcomes:**

* Use `docker ps` to inspect containers
* Understand how container ports map to host ports
* Identify container images and published ports
* Run containers with `-p` and `--name` flags
* Use custom images like `kodekloud/simple-webapp:blue`

---

## 🛠 Step-by-Step Journey

### **Step 1 — Inspect Running Containers**

Command:

```bash
docker ps
```

Number of running containers:

```
1
```

---

### **Step 2 — Identify the Image Used by the Running Container**

From the `IMAGE` column of:

```bash
docker ps
```

Image used:

```
nginx:alpine
```

---

### **Step 3 — Count Unique Ports Published on the Container**

Observed from the `PORTS` column:

```
2 unique ports published
```

---

### **Step 4 — Determine Which Ports Are Exposed Inside the Container**

Based on the container configuration:

**Exposed container ports:**

```
3456
80
```

---

### **Step 5 — Determine Which Ports Are Published on the Host**

Published host ports:

```
30880
3456
```

(As mapped from the container’s port exposure)

---

### **Step 6 — Run a Custom Web App Container with Port Mapping**

Goal:

* Run container using: `kodekloud/simple-webapp:blue`
* Name it: `blue-app`
* Map container port **8080** → host port **38282**

Command:

```bash
docker run -p 38282:8080 --name blue-app kodekloud/simple-webapp:blue
```

Container launched successfully.

---

## 💡 Notes / Tips

* `docker ps` shows only **running** containers — add `-a` to see stopped ones.
* The `-p` flag maps **host:container** ports (host first, container second).
* Images on Docker Hub can be pulled automatically when used in `docker run`.
* Naming containers with `--name` makes management much easier.
* Alpine-based images are lightweight and ideal for quick labs.

---

## 📌 Lab Summary

| Step                          | Status | Key Takeaways                                         |
| ----------------------------- | ------ | ----------------------------------------------------- |
| Check running containers      | ✅      | One container running                                 |
| Identify container image      | ✅      | Using `nginx:alpine`                                  |
| Check published ports         | ✅      | 2 unique ports                                        |
| Identify container-side ports | ✅      | 80 and 3456 exposed                                   |
| Identify host-side ports      | ✅      | Host ports mapped correctly                           |
| Run custom web app container  | ✅      | Port mapping with `-p` and container named `blue-app` |

---

## 🔗 References

* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker run](https://docs.docker.com/engine/reference/run/)
* [Docker port mapping](https://docs.docker.com/network/)
