# 🚀 Next.js + Docker + GitHub Actions + Kubernetes (Minikube) Deployment

This project demonstrates how to containerize a **Next.js** application, build and publish the image using **GitHub Actions** & **GitHub Container Registry (GHCR)**, and deploy it to a local Kubernetes cluster using **Minikube**.

---

## 📦 Tech Stack

- **Next.js** (React framework)
- **Docker** (containerization)
- **GitHub Actions** (CI/CD pipeline)
- **GitHub Container Registry (GHCR)** (image hosting)
- **Kubernetes** (orchestration)
- **Minikube** (local Kubernetes cluster)

---

## 🧰 Setup Instructions

### 1. Clone the Repo
git clone https://github.com/akramsiddiqui2007/nodejs_app.git
cd nodejs_app

### 2. Install Dependencies
npm install
# Local Development
npm run dev
Visit: http://localhost:3000

### Docker
### Build Docker Image
docker build -t my-nextjs-app .

### Run Docker Container
docker run -p 3000:3000 my-nextjs-app

### GitHub Actions CI/CD
### A GitHub Actions workflow is set up to:
### Build Docker image on push to main
### Push the image to GitHub Container Registry (GHCR)

Workflow file: .github/workflows/docker-build.yml

### Ensure your repository has:

✅ Public visibility

✅ Workflow permissions: contents: read, packages: write

📦 GitHub Container Registry
Image URL:
ghcr.io/akramsiddiqui2007/nodejs_app:latest

You can pull it using:


docker pull ghcr.io/akramsiddiqui2007/nodejs_app:latest


###  Deploy to Minikube
1. Start Minikube
minikube start
2. Apply Kubernetes Manifests
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
3. Access the App
minikube service nextjs-service
This will open your app in the browser at a local NodePort.

📂 Kubernetes Files
k8s/deployment.yaml
Deploys 2 replicas

Uses readiness & liveness probes

Pulls image from GHCR

k8s/service.yaml
Exposes the app on a random NodePort

Enables external access via Minikube

📌 Useful Commands
kubectl get pods
kubectl get svc
kubectl logs <pod-name>
kubectl rollout restart deployment nextjs-deployment

🧠 Author
Akram Siddiqui
📧 akramsiddiqui2007@gmail.com

📬 Submission
GitHub Repo: https://github.com/akramsiddiqui2007/nodejs_app

GHCR Image: ghcr.io/akramsiddiqui2007/nodejs_app:latest
