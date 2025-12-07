# Wisecow – DevOps Deployment Project

This repository contains the complete implementation of the **Wisecow application** deployment as part of the AccuKnox DevOps Practical Assessment.
The project includes containerization, Kubernetes deployment on AWS EKS, TLS/HTTPS security, CI/CD automation, and operational monitoring scripts.

---

## 📌 Problem Statement 1 – Implementation Summary

### **Dockerization**

* The Wisecow shell-based application was packaged into a Docker image with all required dependencies.
* The image is pushed to Docker Hub and used by Kubernetes during deployment.

### **Kubernetes Deployment (AWS EKS)**

* A dedicated namespace named `wisecow` was created.
* The application is deployed using a Kubernetes Deployment with multiple replicas.
* A Service exposes the pods internally, and later through AWS LoadBalancer and Ingress.
* EKS cluster access was configured using an IAM user via the `aws-auth` ConfigMap.

### **TLS / HTTPS Integration**

* A TLS certificate was created and stored as a Kubernetes TLS secret.
* NGINX Ingress Controller was installed on the EKS cluster.
* An HTTPS-enabled Ingress rule securely exposes the Wisecow application externally.

### **CI/CD Pipeline (GitHub Actions)**

A fully automated CI/CD workflow is set up to:

* Build the Docker image on every push to the `main` branch
* Push the image to Docker Hub
* Deploy updated Kubernetes manifests automatically to AWS EKS
* Redeploy the application without manual intervention

GitHub Secrets store the credentials for:

* Docker Hub
* AWS IAM user
* EKS access

This completes the full Continuous Integration and Continuous Deployment cycle.

---

## 📌 Problem Statement 2 – Automation Scripts

### **System Health Monitoring**

* A Bash script monitors CPU, memory, disk usage, and running processes.
* It logs alerts when thresholds are exceeded.
* This helps ensure the underlying EC2 host remains stable.

### **Application Health Checker**

* A Python script periodically checks the Wisecow HTTPS endpoint.
* It determines whether the application is UP or DOWN based on HTTP response codes.
* Status is logged with timestamps for observability.

---

## 📁 Repository Structure

The repository contains:

* Dockerfile and application script
* Kubernetes manifests (deployment, service, ingress)
* TLS certificates used for secure ingress
* CI/CD pipeline configuration under `.github/workflows`
* Automation scripts inside `problem-2`

---

## 📸 Screenshots Evidence

All screenshots required for evaluation—including Docker image builds, Docker Hub repository, EKS deployment, pods/services, TLS configuration, Ingress access, CI/CD pipeline runs, and health-check outputs—are available here:

👉 **Google Drive Screenshot Folder:**
**[https://drive.google.com/drive/folders/1nGJ1QZaT4TvDhBCZKnbqBcol_Wm569Q-?usp=sharing](https://drive.google.com/drive/folders/1nGJ1QZaT4TvDhBCZKnbqBcol_Wm569Q-?usp=sharing)**

---

## 🏁 Final Outcome

This project successfully demonstrates:

* End-to-end Docker + Kubernetes deployment
* Secure TLS-enabled ingress via NGINX
* Automated CI/CD using GitHub Actions
* AWS EKS orchestration and access management
* System and application monitoring scripts

All mandatory and optional objectives of the assessment have been fully implemented.

---
