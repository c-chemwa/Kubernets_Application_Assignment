# Widgetario – Kubernetes Hackathon Project

## 🧠 Overview

Widgetario is a microservices-based web application deployed using Kubernetes. It simulates a product listing and stock checking system composed of:

- A PostgreSQL database (`products-db`)
- A Product API (`products-api`)
- A Stock API (`stock-api`)
- A Web frontend (`widgetario-web`)

This project was developed for a Kubernetes Hackathon focused on applying core Kubernetes concepts like Deployments, Services, ConfigMaps, Probes, and Ingress.

---

## 🚀 Features

- 🧱 Microservices architecture
- 🗃️ PostgreSQL-backed data layer
- 🧪 Health and readiness probes
- 🔐 Secrets and ConfigMaps for configuration
- 🌐 Exposed via NodePort/LoadBalancer
- 🎯 Built and deployed locally on Minikube

---

## 📦 Technologies Used

- Kubernetes
- Docker
- PostgreSQL
- Node.js / Express.js (assumed for APIs)
- React / Nginx (assumed for frontend)
- Minikube for local development

---

## 🛠️ Installation & Setup

### Prerequisites

- [Docker](https://www.docker.com/)
- [Minikube](https://minikube.sigs.k8s.io/docs/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

### 1. Start Minikube

```bash
minikube start
