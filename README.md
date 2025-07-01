# Three-Tier Application on Kubernetes

This project deploys a **three-tier application** consisting of:

- 🖼️ Frontend (Node/Vite app)
- ⚙️ Backend (Node.js / Express API)
- 🗄️ MongoDB (as a StatefulSet)

All services are containerized and deployed to a local Kubernetes cluster.

---

## 📦 Prerequisites

- Docker
- Kubernetes (minikube, kind, or kubeadm cluster)
- `kubectl` configured
- Docker images pushed to Docker Hub (e.g., `atharvakulkarni2427/wanderlust-frontend` and `wanderlust-backend`)

---

## 🚀 Deploying the Application

Make sure your YAML files are ready to use | Considering the Docker images are already pushed to the hub:

- `frontend-deployment.yaml`
- `backend-deployment.yaml`
- `mongodb-statefulset.yaml`

### Step 1: Apply All YAMLs

```bash
1. kubectl apply -f mongodb-statefulset.yaml
2. kubectl apply -f backend-deployment.yaml
3. kubectl apply -f frontend-deployment.yaml

Verify this by 
1. kubectl get pods
2. kubectl get svc

🌐 Accessing the Frontend (Port Forward)
Since NodePort may not work on WSL2 or certain setups, use port-forwarding instead:
1. kubectl port-forward service/frontend-service 5173:5173
2. http://localhost:5173

🌐 Accessing the Backend (Port Forward)
Since NodePort may not work on WSL2 or certain setups, use port-forwarding instead:
1. kubectl port-forward service/backend-service 5000:5000
2. http://localhost:5000

💾 MongoDB Setup & Inspection
1. kubectl exec -it mongodb-0 -- mongosh -u <username> -p <password>
2. show dbs
3. use test (or the name of the table that you have set)
4. show collections
5. db.posts.find().pretty()
