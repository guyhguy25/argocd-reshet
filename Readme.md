# ArgoCD Reshet Configuration

This folder contains the ArgoCD configuration files for the Reshet service deployment. ArgoCD uses these configurations to automatically deploy and sync the Reshet application with the Kubernetes cluster.

## Overview

The Reshet service is managed and deployed using GitOps principles through ArgoCD. This repository contains the necessary manifests and configuration files that define the desired state of the application in the Kubernetes cluster.

## Usage

### Building the Docker Image
To build the Docker image for the Reshet service:

```bash
# Navigate to the project directory
cd /path/to/reshet

# Build the Docker image
docker build --build-arg ENV_FILE=.env.reshet.prod -t reshet:latest .

# Optionally, tag with a specific version
docker build --build-arg ENV_FILE=.env.reshet.prod -t reshet:v1.0.0 .

# To push to a registry (if applicable)
docker tag reshet:latest your-registry/reshet:latest
docker push your-registry/reshet:latest
```

Make sure you have the proper Dockerfile in your project root directory before building.

### Accessing the Service

To access the Reshet production service locally, you can use the following port-forwarding command:

```bash
kubectl port-forward -n reshet service/reshet-prod 8081:80
```

This will forward local port 8081 to port 80 of the reshet-prod service, allowing you to access the application at http://localhost:8081.