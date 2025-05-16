# Widgetario: Kubernetes Hackathon Project

This project demonstrates deploying a multi-component application (Widgetario) on Kubernetes using Minikube. It includes microservices for products and stock management, a frontend web interface, and a PostgreSQL database.

## 🧱 Repository Structure

```
hackathon/
├── products-db/
│   └── <K8s manifests for DB>
├── products-api/
│   └── <K8s manifests for Products API>
├── stock-api/
│   └── <K8s manifests for Stock API>
├── web/
│   └── <K8s manifests for Web frontend>
├── ingress/
│   └── <Ingress configuration>
├── config/
│   └── <ConfigMaps and Secrets>
├── production/
│   └── <Hardening manifests>
├── observability/
│   └── <Prometheus, Grafana, etc.>
├── ci-cd/
│   └── <Helm charts, Jenkinsfile, etc.>
project/
files/

```

## 📌 Project Overview

Widgetario is a containerized microservices app deployed and managed on Kubernetes. It features:

- **products-db**: PostgreSQL database
- **products-api**: RESTful API to access product data
- **stock-api**: Service managing stock levels
- **web**: Frontend for users
- Kubernetes concepts: Deployments, Services, Ingress, ConfigMaps, Secrets, NodePorts, LoadBalancer, Observability, CI/CD

## ⚙️ Installation and Setup

### Prerequisites

- Docker
- Minikube
- kubectl

### Steps

1. **Start Minikube**

```bash
minikube start
```

2. **Set Docker env to Minikube**

```bash
eval $(minikube docker-env)
```

3. **Apply Kubernetes Manifests (Part 1)**

```bash
kubectl apply -f solution-part-1/products-db \
               -f solution-part-1/products-api \
               -f solution-part-1/stock-api \
               -f solution-part-1/web
```

4. **Check Services**

```bash
kubectl get services
```

Look for `widgetario-web-np` (NodePort) or `widgetario-web-lb` (LoadBalancer).

5. **Access Web App**

```bash
minikube ip
# Example Output: 192.168.49.2

# If NodePort exposed on 30008
http://192.168.49.2:30008
```

---

## 🛠️ Code Documentation

Each deployment and service YAML is commented to explain key fields. All files follow consistent naming, indentation, and structure.

## ✅ Testing

### Manual Testing

Once deployed, access the frontend via the IP and port above. Verify:
- Product list loads
- Stock API responds correctly
- Database is connected

### Optional: Automated Testing

Add unit tests to each microservice and expose health-check endpoints. Include testing commands and results in future development.

## 🚀 Deployment Instructions

1. Ensure Docker images are built and available to Minikube:
   ```bash
   eval $(minikube docker-env)
   docker build -t products-api ./products-api
   docker build -t stock-api ./stock-api
   docker build -t web ./web
   ```

2. Apply all manifests (as shown above).

3. Access the app using `minikube ip` + exposed port.

## 📊 Additional Materials

- Observability setup: Prometheus, Grafana (in `/observability`)
- Production best practices: Resource limits, readiness probes (`/production`)
- Configurations: ConfigMaps & Secrets (`/config`)
- Ingress and Load Balancing (`/ingress`)
- CI/CD pipeline: Helm, Jenkinsfile (`/ci-cd`)

## 🔓 Repository Access

Ensure this repository is public **or** that required users are invited with appropriate permissions.

---

## 🙌 Acknowledgments

- Kubernetes
- Minikube
- Docker
- Prometheus + Grafana
- Jenkins + Helm
