# 🚀 DevStream – DevOps Pipeline Monitoring System

DevStream is a **pipeline monitoring platform** that helps engineering teams track, visualize, and manage their CI/CD workflows.  
It integrates with **GitHub** for pipeline triggers, **Docker** for isolated execution, and provides real-time monitoring via both a **web dashboard**.

---

## 📖 Project Overview

### What is DevStream?

DevStream is a **DevOps pipeline monitoring system**. It allows teams to:

- Define and execute pipelines triggered by GitHub events.
- Visualize pipeline runs in a real-time dashboard.
- Track pipeline health, success/failure rates, and execution logs.

---

## ✨ Features

- 📊 **Dashboard Monitoring** – Real-time pipeline visualization (stages, logs, success/failure rate).
- ⚡ **GitHub Integration** – Auto-trigger pipelines from repo pushes & PRs.
- 🔔 **Notifications** – Web Based Alerts.
- 🐳 **Isolated Execution** – Runs pipelines securely inside Docker containers.
- 👤 **Multi-user Support** – JWT authentication, role-based access.

---

## 🛠️ Tech Stack

- **Backend:** Node.js, Express, TypeScript, MongoDB, Redis, BullMQ
- **Frontend:** React (Vite), TypeScript, Tailwind
- **Infra:** Docker, Render (PaaS) deployment
- **CI/CD:** GitHub Actions

---

## 📂 Project Structure

```
devstream/
├── backend/       # Express API + pipeline engine
├── frontend/      # React dashboard
├── infra/         # Deployment configs
└── cicd/          # GitHub Actions pipelines
```

---

## ⚙️ Local Development Setup

### 1️⃣ Clone Repo

```bash
git clone https://github.com/<your-org>/devstream.git
cd devstream
```

### 2️⃣ Setup Environment Variables

Copy `.env.example` → `.env` and fill in:

```env
MONGODB_URI=mongodb://mongo:27017/devstream
REDIS_URL=redis://redis:6379
JWT_SECRET=supersecret
GITHUB_WEBHOOK_SECRET=your_secret
```

### 3️⃣ Run with Docker Compose

```bash
docker-compose up --build
```

This starts:

- Backend API → `http://localhost:5000`
- Frontend Dashboard → `http://localhost:5173`
- MongoDB + Redis

---

## ☁️ Deployment on Render

### 1️⃣ Backend

- Create a **Render Web Service** → connect to `backend/Dockerfile`
- Add environment variables from `.env.example`
- Deploy service → Auto-deploy on GitHub push

### 2️⃣ Frontend

- Create another **Render Web Service** → connect to `frontend/Dockerfile`
- Add `VITE_API_URL=https://<backend-service>.onrender.com`
- Deploy service

### 3️⃣ Database & Cache

- Add **Render MongoDB instance**
- Add **Render Redis instance**
- Update `MONGODB_URI` and `REDIS_URL` in Render env vars

---

## 🔄 CI/CD with GitHub Actions

CI/CD is managed with workflows in `cicd/github-actions/`:

- `backend.yml` → Lint, test, build, deploy backend.
- `frontend.yml` → Build & deploy frontend.
- `docker-build.yml` → Build & push Docker images.

Pushes to `main` branch automatically trigger deployments.

---

## ✅ Roadmap

- [ ] Advanced analytics (MTTR, deployment frequency, failure rates).
- [ ] Role-based access control (RBAC).
- [ ] Kubernetes-based stage execution.
- [ ] Slack/Discord integrations.

---

## 👨‍💻 Contributors

- **Yuvraj** – Fullstack + DevOps
- Open for contributions 🚀
