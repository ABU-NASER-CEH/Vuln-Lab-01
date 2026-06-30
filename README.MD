# Vuln-Lab-01

A local Docker-based vulnerable lab for practicing web application security, Linux privilege escalation, penetration testing, exploit development, and security research.

> **⚠️ Warning**
>
> This project intentionally contains vulnerable applications. **Run it only on your local machine or in an isolated lab environment.** Never expose these services to the public Internet.

---

# Included Labs

| Application                            | Purpose                             | Local URL            |
| -------------------------------------- | ----------------------------------- | -------------------- |
| WebGoat                                | OWASP security training platform    | http://127.0.0.1/    |
| DVWA (Damn Vulnerable Web Application) | Web vulnerability practice          | http://127.0.0.1:81/ |
| bWAPP                                  | Buggy Web Application               | http://127.0.0.1:82/ |
| OWASP Juice Shop                       | Modern vulnerable web application   | http://127.0.0.1:83/ |
| Linux Privilege Escalation Lab         | Linux privilege escalation practice | SSH on port **2222** |

---

# Repository Structure

```
.
├── docker-compose.yaml
├── Dockerfile
├── entrypoint.sh
├── kernel_challenge.c
├── status_check.c
├── systemctl_mock.sh
└── README.md
```

---

# Requirements

* Docker Engine
* Docker Compose (v2 recommended)

Verify installation:

```bash
docker --version
docker compose version
```

---

# Getting Started

Clone the repository:

```bash
git clone https://github.com/ABU-NASER-CEH/Vuln-Lab-01.git
cd Vuln-Lab-01
```

Build and start everything:

```bash
docker compose up -d --build
```

Check running containers:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs -f
```

Stop the lab:

```bash
docker compose down
```

Stop and remove volumes:

```bash
docker compose down -v
```

---

# Accessing the Labs

## 1. WebGoat

URL:

```
http://127.0.0.1/
```

Management port:

```
127.0.0.1:8090
```

WebGoat may require you to visit the application once before starting lessons.

Documentation:

https://hub.docker.com/r/webgoat/webgoat

---

## 2. DVWA

URL:

```
http://127.0.0.1:81/
```

The MariaDB database is automatically started by Docker Compose.

Official Image:

https://hub.docker.com/r/vulnerables/web-dvwa

---

## 3. bWAPP

URL:

```
http://127.0.0.1:82/
```

After the first startup, complete installation by visiting:

```
http://127.0.0.1:82/install.php
```

Official Image:

https://hub.docker.com/r/hackersploit/bwapp-docker

---

## 4. OWASP Juice Shop

URL:

```
http://127.0.0.1:83/
```

Official Image:

https://hub.docker.com/r/bkimminich/juice-shop

---

## 5. Linux Privilege Escalation Lab

SSH:

```text
127.0.0.1:2222
```

This custom container is built from the repository Dockerfile and includes intentionally insecure configurations for Linux privilege escalation practice.

### Files Included

* `entrypoint.sh`
* `kernel_challenge.c`
* `status_check.c`
* `systemctl_mock.sh`

These components simulate common privilege escalation scenarios.

### 🌐 Connection & Credentials

| Target User | Connection Method                                 | Password     | Initial Access                            |
| ----------- | ------------------------------------------------- | ------------ | ----------------------------------------- |
| **student** | `ssh student@localhost -p 2222`                   | `student123` | Low-privileged SSH access                 |
| **student** | `docker exec -it linux-priv-esc-lab su - student` | N/A          | Interactive terminal inside the container |

> **Note:** The SSH service is exposed on host port **2222**. If you're running the lab locally, connect using `localhost` or `127.0.0.1`.

---

# Docker Services

| Service       | Internal Port | Host Port |
| ------------- | ------------- | --------- |
| WebGoat       | 8080          | 80        |
| WebGoat Admin | 9090          | 8090      |
| DVWA          | 80            | 81        |
| bWAPP         | 80            | 82        |
| Juice Shop    | 3000          | 83        |
| Linux SSH     | 22            | 2222      |

---

# Docker Compose

The lab consists of:

* WebGoat
* DVWA
* MariaDB
* bWAPP
* OWASP Juice Shop
* Custom Linux Privilege Escalation Lab

Persistent storage is used for:

```
dvwa-db
```

---

# Useful Docker Commands

Start:

```bash
docker compose up -d
```

Rebuild:

```bash
docker compose up -d --build
```

Restart:

```bash
docker compose restart
```

Stop:

```bash
docker compose down
```

Remove volumes:

```bash
docker compose down -v
```

View logs:

```bash
docker compose logs
```

Logs for one container:

```bash
docker compose logs webgoat
```

Open a shell:

```bash
docker compose exec linux_priv_lab bash
```

---

# Learning Objectives

This lab can be used to practice:

* SQL Injection
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Authentication bypass
* Command Injection
* File Inclusion
* File Upload vulnerabilities
* Insecure Direct Object Reference (IDOR)
* Server-Side Request Forgery (SSRF)
* Session attacks
* Privilege Escalation
* Linux Enumeration
* Kernel Exploitation
* Docker Security
* Web Penetration Testing
* Capture the Flag (CTF) practice

---

# Security Notice

This repository intentionally contains insecure software.

**Do not:**

* Deploy on a public server.
* Expose ports to the Internet.
* Use on production infrastructure.
* Store sensitive information inside the containers.

Use only in isolated virtual machines or lab environments.

---

# References

WebGoat

https://hub.docker.com/r/webgoat/webgoat

DVWA

https://hub.docker.com/r/vulnerables/web-dvwa

bWAPP

https://hub.docker.com/r/hackersploit/bwapp-docker

OWASP Juice Shop

https://hub.docker.com/r/bkimminich/juice-shop

Linux Privilege Escalation Docker Lab Inspiration

https://github.com/haltacademy/Linux-Privilege-Escalation-Docker-Lab

---

# License

This project is intended for educational and security research purposes only.

Use responsibly.

