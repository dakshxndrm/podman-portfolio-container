# 🚀 Portfolio Website using Podman + Nginx

This project shows how to containerize and run a static portfolio website using **Podman** and **Nginx**, with optional systemd auto-start.

---

## 📌 Features

* Rootless container using Podman
* Lightweight Nginx server
* Easy deployment on localhost
* Systemd service for auto-start
* Docker Hub image support

---

## 📁 Project Structure

```
portfolio-project/
│── index.html
│── style.css
│── Dockerfile
│── README.md
```

---

## ⚙️ Prerequisites

* Linux system
* Podman installed
* Basic terminal knowledge

---

## 🚀 How to Run the Project

### 1. Clone Repository

```
git clone https://github.com/your-username/portfolio-container.git
cd portfolio-container
```

---

### 2. Build Image

```
podman build -t portfolio-site .
```

---

### 3. Run Container

```
podman run -d -p 8080:80 --name portfolio-container portfolio-site
```

---

### 4. Open in Browser

```
http://localhost:8080
```

---

## ✏️ How to Make Changes

### 🔹 Edit Website Content

Modify:

* `index.html` → structure/content
* `style.css` → design/styling

After changes:

```
podman build -t portfolio-site .
podman stop portfolio-container
podman rm portfolio-container
podman run -d -p 8080:80 --name portfolio-container portfolio-site
```

---

### 🔹 Live Editing (No Rebuild Required)

```
podman run -d -p 8080:80 \
-v $(pwd):/usr/share/nginx/html:Z,ro \
nginx:alpine
```

👉 Now changes reflect instantly.

---

## 🔄 Run as Background Service (Optional)

Generate systemd service:

```
podman generate systemd --new --name portfolio-container --files --restart-policy=always
```

Move service:

```
mkdir -p ~/.config/systemd/user
mv container-portfolio-container.service ~/.config/systemd/user/
```

Enable service:

```
systemctl --user daemon-reload
systemctl --user enable --now container-portfolio-container.service
```

---

## ☁️ Docker Hub (Optional)

### Push Image

```
podman login docker.io
podman tag portfolio-site docker.io/your-username/portfolio-site
podman push docker.io/your-username/portfolio-site
```

### Pull & Run

```
podman pull docker.io/your-username/portfolio-site
podman run -d -p 8080:80 docker.io/your-username/portfolio-site
```

---

## 🛑 Stop Container

```
podman stop portfolio-container
podman rm portfolio-container
```

---

## 🔥 Improvements You Can Add

* Add **HTTPS** using reverse proxy (Nginx + SSL)
* Deploy on a cloud server (AWS / VPS)
* Add custom domain
* Use CI/CD (GitHub Actions)
* Improve UI with animations (CSS/JS)
* Convert to full-stack (backend + database)

---


## 🧠 Learning Outcome

* Containerization using Podman
* Image building and deployment
* Service automation using systemd
* Basic DevOps workflow

---

## 📬 Contribution

Feel free to fork and improve this project.
