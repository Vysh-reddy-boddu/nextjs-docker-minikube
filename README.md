# Next.js Application – Containerized & Deployed on Kubernetes

This repository contains a **Next.js** application that has been containerized using **Docker**, automated with **GitHub Actions** for image build and push to **GitHub Container Registry (GHCR)**, and deployed to **Kubernetes** using **Minikube**.

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Prerequisites](#prerequisites)  
- [Local Setup](#local-setup)  
- [Dockerization](#dockerization)  
- [GitHub Actions Workflow](#github-actions-workflow)  
- [Kubernetes Deployment](#kubernetes-deployment)  
- [Accessing the Application](#accessing-the-application)  
- [Repository Structure](#repository-structure)

---

## Project Overview

- **Framework:** Next.js  
- **Containerization:** Docker  
- **CI/CD:** GitHub Actions  
- **Container Registry:** GitHub Container Registry (GHCR)  
- **Local Kubernetes:** Minikube  

This project demonstrates an end-to-end workflow of building, containerizing, and deploying a Next.js app in a Kubernetes cluster.

---

## Prerequisites

Ensure the following tools are installed:

- Node.js (v18+) and npm  
- Docker  
- Minikube  
- kubectl  
- Git  

---

## Local Setup

1. Clone the repository:

```bash
git clone https://github.com/Vysh-reddy-boddu/nextjs-docker-minikube.git
cd nextjs-docker-minikube


2. Install dependencies:

```bash
npm install

3. Run the development server:

```bash
npm run dev

4. Open http://localhost:3000 in your browser.

## Dockerization

1. Build the Docker image:

```bash
docker build -t nextjs-app:latest .

2. Run the Docker container locally:

```bash
docker run -p 3000:3000 nextjs-app:latest

3. Open http://localhost:3000 in your browser


---

```markdown
## GitHub Actions Workflow

The project uses GitHub Actions to automate:

1. Build Docker image on push to the `main` branch.
2. Push the image to GitHub Container Registry (GHCR).

Workflow file: `.github/workflows/docker-publish.yml`

- Logs in to GHCR using a Personal Access Token.
- Builds the Docker image.
- Pushes the image with the `latest` tag.

## Kubernetes Deployment

The Kubernetes manifests are in the `k8s/` folder:

- `deployment.yaml`: Defines 2 replicas with readiness and liveness probes.
- `service.yaml`: Exposes the app via NodePort.

Deploy to Minikube:

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

Check pods and service:

```bash 
kubectl get pods
kubectl get svc


---

```markdown
## Accessing the Application

1. Run the following command to open the service in your browser:

```bash
minikube service nextjs-service

2. Minikube will display the URL with the NodePort mapping. Open it to see your Next.js app.
