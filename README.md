<<<<<<< HEAD
# CI-CD-Test
testing
=======
# Complete CI/CD Pipeline Setup Using GitHub Actions & Self-Hosted Runner (Production-Ready Guide)

A fully production-grade CI/CD pipeline using GitHub Actions, Docker, Docker Compose, and a self-hosted GitHub runner. This guide shows how to automate **build → push → deploy → health check → rollback** without downtime.

This tutorial is perfect for **DevOps engineers**, **backend developers**, **SRE teams**, and anyone wanting to build a secure, fast, and scalable CI/CD system.

---

## 📌 Why This CI/CD Setup Is Better?

This workflow:

- 🚀 Deploys services instantly after a push
- 🔒 Uses GitHub Actions Self-Hosted Runner for secure deployments
- 🔄 Automatically updates Docker Compose
- ✅ Performs a full health check
- 🔙 Does auto rollback if deploy fails
- ⏱ Reduces downtime to near-zero
- 🛠 Works for any microservice or containerized app

This is one of the most complete, production-level CI/CD examples available publicly.

---

## 🔍 What You Will Learn (Highly Searched Topics)

- How to set up GitHub self-hosted runner
- How to create CI/CD pipeline with GitHub Actions
- Docker-based deployment automation
- Zero-downtime deployment using Docker Compose
- Rollback strategy in CI/CD
- Health check automation for Docker containers
- Best practice folder structure for DevOps projects

This repository demonstrates a **production-ready deployment workflow** for any Dockerized microservice.

---

## 📑 Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Architecture Diagram](#architecture-diagram)  
- [Prerequisites](#prerequisites)  
- [1. Setup Self-Hosted Runner](#1-setup-self-hosted-runner)  
- [2. Configure GitHub Repository](#2-configure-github-repository)  
- [3. CI/CD Workflow File](#3-cicd-workflow-file)  
- [4. Deployment Flow](#4-deployment-flow)  
- [5. Rollback Logic](#5-rollback-logic)  
- [6. Folder Structure](#6-folder-structure)  

---

## 🔍 Overview

This CI/CD pipeline automatically:

1. 🛠 Builds a Docker image  
2. 📤 Pushes it to a container registry  
3. 📥 Pulls the latest version on the server  
4. 🔄 Updates `docker-compose.yml` with the new tag  
5. 🚀 Starts the service with minimal downtime  
6. ✅ Performs a health check  
7. 🔙 Rolls back automatically on failure  

Designed for **real production use**.

---

## ⭐ Features

✔ Self-hosted secure deployment  
✔ Full CI + CD  
✔ Automatic backup of `docker-compose`  
✔ Rollback on failed deployment  
✔ Health-check monitoring  
✔ Logs printed directly in GitHub Actions  
✔ Zero-downtime container restart  
✔ Easy to extend for multiple services  

---

## 🏗 Architecture Diagram (Placeholder)

```
[ Developer Push ]
       |
       v
[ GitHub Actions - CI ]
       |
       v
[ Registry (Docker Hub / GHCR) ]
       |
       v
[ GitHub Actions - CD (Self-Hosted Runner) ]
       |
       v
[ Server ]
       | |
       | Build New Container
       | |
       | Health Check
       | |
       |-> Rollback if Failed
       |
Deploy Successful
```

---

## 🧩 Prerequisites

- Linux server (Ubuntu recommended)  
- Docker & Docker Compose  
- GitHub repository  
- Docker registry credentials  
- Self-hosted runner machine  

---

## 1️⃣ Setup Self-Hosted Runner

Create a directory:

```bash
mkdir -p /home/deployer/actions-runner
cd /home/deployer/actions-runner
```

Download runner:

```bash
curl -L -o actions-runner-linux-x64.tar.gz \
https://github.com/actions/runner/releases/latest/download/actions-runner-linux-x64.tar.gz

tar xzf actions-runner-linux-x64.tar.gz
```

---

## 2️⃣ Configure GitHub Repository

1. Go to: **Settings → Actions → Runners → New self-hosted runner**
2. Select **Linux**
3. Copy the provided configuration command
4. Run it on your server as a dedicated user (recommended: `deployer`)
5. Start the runner:

```bash
./run.sh
```

Run as Background Service:

```bash
sudo ./svc.sh install
sudo ./svc.sh start
sudo ./svc.sh status
```

---

## 🔄 Rollback Logic

If the container becomes unhealthy, the system will:

- Restore previous `docker-compose.yml`
- Restart the service
- Mark the workflow as failed
- Notify via GitHub Alerts

---

## 🎉 Result

- Once you push to the selected branch:
  - Docker image builds
  - Image pushes to registry
  - Server auto-deploys
  - Health check validates
  - Rollback occurs if needed

This creates a robust & production-ready CI/CD pipeline for any Docker service.

