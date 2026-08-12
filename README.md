# 🚀 CloudDeploy — Kubernetes CI/CD Deployment

A complete DevOps project demonstrating how to build, containerize, continuously integrate, and deploy a web application using **GitHub Actions, Docker, Docker Hub, and Kubernetes (kind)**.

The project also demonstrates important Kubernetes capabilities such as **replicas, self-healing, rolling updates, and rollback**.

---

## 🏗️ Architecture

```text
                    Developer
                        │
                        │ git push
                        ▼
                ┌───────────────┐
                │    GitHub     │
                │  Repository   │
                └───────┬───────┘
                        │
                        ▼
                ┌───────────────┐
                │ GitHub Actions│
                │     CI/CD     │
                └───────┬───────┘
                        │
                  Docker Build
                        │
                        ▼
                ┌───────────────┐
                │   Docker Hub  │
                │ clouddeploy   │
                │  v1 / v2      │
                └───────┬───────┘
                        │
                   Image Pull
                        │
                        ▼
              ┌────────────────────┐
              │   kind Cluster     │
              │                    │
              │  ┌──────────────┐  │
              │  │  Deployment  │  │
              │  │ replicas: 2  │  │
              │  └──────┬───────┘  │
              │         │           │
              │    ┌────┴────┐      │
              │    ▼         ▼      │
              │  Pod v1    Pod v1   │
              │    │         │      │
              │    └────┬────┘      │
              │         ▼           │
              │      Service        │
              │     NodePort        │
              └─────────┬──────────┘
                        │
                        ▼
                 Web Application
