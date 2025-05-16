# Widgetario: Kubernetes Hackathon Project

This project demonstrates deploying a multi-component application (Widgetario) on Kubernetes using Minikube. It includes microservices for products and stock management, a frontend web interface, and a PostgreSQL database.

---

## 🧱 Repository Structure

solution-part-1/
├── products-db/
│ └── <K8s manifests for DB>
├── products-api/
│ └── <K8s manifests for Products API>
├── stock-api/
│ └── <K8s manifests for Stock API>
├── web/
│ └── <K8s manifests for Web frontend>
solution-part-2/
├── ingress/
│ └── <Ingress configuration>
├── config/
│ └── <ConfigMaps and Secrets>
├── production/
│ └── <Hardening manifests>
├── observability/
│ └── <Prometheus, Grafana, etc.>
├── ci-cd/
│ └── <Helm charts, Jenkinsfile, etc.>

yaml
Copy
Edit

---

## 📌 Project Overview

Widgetario is a containerized microservices app deployed and managed on Kubernetes. It features:

- **products-db**: PostgreSQL database  
- **products-api**: RESTful API to access product data  
- **stock-api**: Service managing stock levels  
- **web**: Frontend for users  

Kubernetes concepts used:

- Deployments, Services  
- Ingress, ConfigMaps, Secrets  
- NodePorts, LoadBalancer  
- Observability (Prometheus/Grafana)  
- CI/CD (Helm, Jenkins)  

---

## ⚙️ Installation and Setup

### Prerequisites

- Docker  
- Minikube  
- kubectl  

### Steps

1. **Start Minikube**

```bash
minikube start
Set Docker environment to Minikube

bash
Copy
Edit
eval $(minikube docker-env)
Apply Kubernetes Manifests (Part 1)

bash
Copy
Edit
kubectl apply -f solution-part-1/products-db \
               -f solution-part-1/products-api \
               -f solution-part-1/stock-api \
               -f solution-part-1/web
Check Services

bash
Copy
Edit
kubectl get services
Look for widgetario-web-np (NodePort) or widgetario-web-lb (LoadBalancer).

Access Web App

bash
Copy
Edit
minikube ip
# Example Output: 192.168.49.2

# If NodePort exposed on 30008
http://192.168.49.2:30008
🛠️ Code Documentation
Each Kubernetes manifest is documented using inline comments to explain:

Key fields like metadata, spec, selector, etc.

Relationships between services, deployments, and pods

Port mappings and access types

All YAML files follow clean formatting and consistent naming conventions.

✅ Testing
Manual Testing
After deployment, visit the frontend via the exposed IP and port:

Confirm products list displays

Confirm stock service updates/reads correctly

Ensure no errors in logs for any pod

Use kubectl logs <pod-name> for debugging

Optional: Automated Testing
Add health check routes in services and CI tests in the /ci-cd stage.

🚀 Deployment Instructions
Ensure Docker images are built and available to Minikube

bash
Copy
Edit
eval $(minikube docker-env)

# Build the images
docker build -t products-api ./products-api
docker build -t stock-api ./stock-api
docker build -t web ./web
Apply manifests

bash
Copy
Edit
kubectl apply -f solution-part-1/products-db \
               -f solution-part-1/products-api \
               -f solution-part-1/stock-api \
               -f solution-part-1/web
Access via browser

bash
Copy
Edit
minikube ip
# Visit with IP:PORT (e.g., http://192.168.49.2:30008)
📊 Additional Materials
Observability: Prometheus + Grafana dashboards (/observability)

Production configs: Readiness probes, resource limits (/production)

Secrets & ConfigMaps: Loaded via /config

Ingress & Routing: /ingress contains ingress YAML

CI/CD Setup: Helm charts, Jenkinsfile (/ci-cd)

🔓 Repository Access
Ensure this repo is public or that your reviewer has access if private.
All files should be committed, structured cleanly, and documented.

🙌 Acknowledgments
Kubernetes

Minikube

Docker

Prometheus + Grafana

Jenkins + Helm
