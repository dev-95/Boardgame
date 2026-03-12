# 🎲 BoardgameListingWebApp: End-to-End DevOps Implementation

> A Java Full-Stack Web Application deployed through a complete, automated DevOps pipeline — from code push to live Kubernetes cluster on Azure, with zero manual intervention.

---

## 🚀 Live Demo

> **Note:** Hosted on an Azure VM via Minikube NodePort.

---

## 📖 Project Overview

This project takes an existing Java Spring Boot board game management application and implements a **production-grade DevOps lifecycle** around it — containerizing the app, automating builds via CI/CD, and orchestrating deployments on Kubernetes running on Microsoft Azure.

The application supports role-based access control, allowing different user types to view, add, edit, and delete board game listings and reviews.

### The Goal
Demonstrate industry-standard DevOps automation: a developer pushes code → GitHub Actions builds and tests → Docker image is versioned and pushed → Kubernetes automatically updates the live site. No manual steps.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Application | Java 11, Spring Boot, Thymeleaf, Spring Security, H2 Database |
| Build Tool | Maven |
| Containerization | Docker (multi-stage build) |
| Container Registry | Docker Hub (`devesh0905/boardgame:v1`) |
| CI/CD | GitHub Actions |
| Orchestration | Kubernetes (Minikube on Azure VM) |
| Cloud Provider | Microsoft Azure |

---

## 🏗️ DevOps Architecture & Workflow

```
Code Push → GitHub Actions → Maven Build & Test → Docker Image → Docker Hub → Kubernetes → Live App
```

| Stage | Description |
|-------|-------------|
| **Source Control** | Code versioned and managed in GitHub |
| **CI — Build & Test** | GitHub Actions triggers on every push to `main`, runs Maven tests and builds the JAR |
| **Containerization** | Multi-stage Dockerfile packages the Spring Boot JAR into a lightweight production image |
| **Registry** | Versioned images pushed to Docker Hub automatically |
| **Orchestration** | Kubernetes manages 2 replicas for high availability and self-healing |
| **Cloud** | Minikube cluster running on an Azure VM, exposed via NodePort with Azure NSG rules |

---

## 🔐 Role-Based Access Control

| Role | Credentials | Permissions |
|------|-------------|-------------|
| Non-Member | *(no login required)* | View board game lists and reviews |
| User | `bugs` / `bunny` | Add board games and write reviews |
| Manager | `daffy` / `duck` | Edit and delete reviews |

---

## 🚦 How to Run

### Option 1 — Run Locally

```bash
mvn clean package
java -jar target/database_service_project-0.0.7.jar
```

Then open `http://localhost:8080` in your browser.

### Option 2 — Deploy to Kubernetes

Ensure your cluster is running, then apply the manifests:

```bash
kubectl apply -f deployment-service.yaml
```

Verify pods are running:

```bash
kubectl get pods
kubectl get svc
```

---

## 📈 Key DevOps Skills Demonstrated

- **CI/CD Automation** — GitHub Actions pipeline reduces deployment from manual steps to fully automated on every push
- **Containerization** — Multi-stage Docker build produces a minimal, production-ready image
- **Kubernetes Orchestration** — 2-replica deployment with self-healing and rolling update support
- **Cloud Networking** — Azure NSG rules configured to allow external traffic to the Kubernetes NodePort
- **Infrastructure as Code** — Kubernetes resources defined and managed entirely via YAML manifests

---

## 📁 Project Structure

```
.
├── src/                          # Java Spring Boot application source
├── Dockerfile                    # Multi-stage Docker build
├── deployment-service.yaml       # Kubernetes Deployment + Service manifest
├── .github/workflows/            # GitHub Actions CI/CD pipeline
├── pom.xml                       # Maven build configuration
└── .gitignore                    # Excludes build artifacts and secrets
```

---

## 👤 Author

**Devesh Chowdary Chalasani**  
Cloud & DevOps Engineer  
[LinkedIn](https://linkedin.com/in/devesh-chalasani) · [Docker Hub](https://hub.docker.com/u/devesh0905)
