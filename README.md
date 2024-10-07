# Weather App

This repository contains the necessary files and configuration for deploying the Weather App. It includes Docker, Jenkins CI/CD pipeline, and Kubernetes deployment configurations.

## Features

- **Dockerfile**: Build the application's Docker image.
- **Jenkinsfile**: Automates the process of building, testing, and deploying the application using Jenkins.
- **Kubernetes Configurations**: YAML files for deployment, service, and namespace.

## Requirements

- Docker installed locally
- Jenkins server set up with access to the GitHub repository
- Kubernetes cluster available for deployment
- Access to a Docker registry (e.g., Docker Hub, AWS ECR, etc.)

## Project Structure

-Html,Css and Javascript simple project for weather app by calling Api 

## Docker

### Building the Docker Image

To build the Docker image for the Weather App:

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/Weather-App.git
   cd Weather-App
   
2. build image and push to docker registry to be puplic
    ```bash
    docker build -t weather-image:latest .
    docker tag weather-app:latest your-docker-repo/weather-app:latest
    docker push your-docker-repo/weather-app:latest

## Jenkins

### Jenkinsfile Configuration
- Here’s an outline of the steps in the Jenkinsfile:

- Clone the Repository: Jenkins pulls the latest code from GitHub.
- Build Docker Image: Jenkins builds the Docker image using the Dockerfile.
- Pull Docker Image: Jenkins pulls the built image from a Docker registry.
- create docker container from pulled image 

# Setup Instructions for Jenkins
1. To set up the Jenkins pipeline:

- Ensure you have a Jenkins server with the following plugins installed:

- Git: For cloning the repository.
- Docker Pipeline: For building and pushing Docker images.
- take jenkins file and put it in the pipline in jenkins and build job 

## Kubernates 
The k8s folder contains the Kubernetes configuration files necessary to deploy the Weather App in a Kubernetes cluster.

### Deployment YAML
- deployment.yaml: Defines the pod specification and the desired replica count for the application.
### Service YAML
- service.yaml: Exposes the application as a service, allowing external access via a LoadBalancer or NodePort.
### Namespace YAML
- namespace.yaml: Defines the namespace where the application will run in the Kubernetes cluster.

## Those are the commands to Create namespace , deploy application , expose service and Verify that the pods and services are running:
    ```bash
    kubectl apply -f k8s/namespace.yaml
    kubectl apply -f k8s/deployment.yaml
    kubectl apply -f k8s/service.yaml
    kubectl get pods -n weather-app-namespace
    kubectl get services -n weather-app-namespace


