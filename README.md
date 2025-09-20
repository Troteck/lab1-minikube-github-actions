# 🚀 Lab1: Continuous Deployment Using GitHub Actions with Minikube

## 🎯 Overview

This project demonstrates how to set up a continuous deployment pipeline for a simple Node.js application using GitHub Actions and Minikube. Minikube allows running a local Kubernetes cluster for testing and development, making it ideal for verifying deployments without needing a remote cluster.

The workflow builds a Docker image of the Node.js app, starts a Minikube cluster in the GitHub Actions environment, deploys the app to it, and tests the service. This ensures the code works correctly before potential promotion to production.

The project is based on a lab task to deploy a "Hello World" Node.js app to Minikube via GitHub Actions. All steps have been implemented and verified successfully.

## ✨ Prerequisites

- Docker (or a compatible container runtime) installed locally if running Minikube outside of GitHub Actions.
- Minikube installed (follow instructions at [minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)).
- Kubernetes CLI (`kubectl`) for interacting with the cluster.
- GitHub account and repository setup.

In GitHub Actions, the workflow uses the `medyagh/setup-minikube` action to handle Minikube setup automatically.

## 📁 Project Structure

- **Dockerfile**: Defines the Docker image for the Node.js app.
- **package.json**: Dependencies and scripts for the app.
- **server.js**: The main Node.js application file serving a "Hello World" response.
- **k8s-node-app.yaml**: Kubernetes manifests for Deployment and Service.
- **.github/workflows/deploy-to-minikube-github-actions.yaml**: GitHub Actions workflow for building, deploying, and testing.

## 💡 Usage

1. Clone the repository:
   ```
   git clone https://github.com/Troteck/lab1-minikube-github-actions.git
   cd lab1-minikube-github-actions
   git checkout develop
   ```

2. Push changes to trigger the workflow (or run it manually via GitHub Actions tab).

3. Check the Actions tab in your GitHub repository to verify the job status. A successful run indicates the app was built, deployed to Minikube, and the service URL was generated for testing.

## ✅ Verification

The workflow has been tested and runs successfully. It starts Minikube, builds the Docker image, deploys the Kubernetes resources, and outputs the service URL. You can view the logs in GitHub Actions for details like pod status and service endpoints.

For local testing:
- Start Minikube: `minikube start`
- Build the image: `docker build -t devopshint/node-app:latest .`
- Deploy: `kubectl apply -f k8s-node-app.yaml`
- Get the URL: `minikube service nodejs-app --url`
- Access the app in your browser to see "Hello World".

## 📚 Resources

- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/start/)
- [Setup Minikube Action](https://github.com/marketplace/actions/setup-minikube)

This lab covers deploying a Node.js app to Minikube using GitHub Actions, ensuring automated testing in a local Kubernetes environment.