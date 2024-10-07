
# Weather App

This repository contains the necessary files and configuration for deploying the Weather App, including Docker, Jenkins CI/CD pipeline, and Kubernetes deployment configurations.

## Features
- **WeatherApp**: weather application with html,css and javascript to view weather of any country 
- **Dockerfile**: Build the application's Docker image.
- **Jenkinsfile**: Automates the process of building, testing, and deploying the application using Jenkins.
- **Kubernetes Configurations**: YAML files for deployment, service, and namespace setup in a Kubernetes cluster.

## Requirements

- Docker installed locally.
- Jenkins server set up with access to the GitHub repository.
- Kubernetes cluster available for deployment.
- Access to a Docker registry (e.g., Docker Hub, AWS ECR).

## Project Structure

A simple weather application built with HTML, CSS, and JavaScript by making API calls to fetch weather data.

```
├── Dockerfile
├── Jenkinsfile
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── namespace.yaml
├── index.html
├── styles.css
└── app.js
```

## Docker

### Building the Docker Image

To build the Docker image for the Weather App:

1. Clone this repository:
    ```bash
    git clone https://github.com/SalmHossam/Weather-App.git
    cd Weather-App
    ```

2. Build the Docker image and push it to a public Docker registry:
    ```bash
    docker build -t weather-app:latest .
    docker tag weather-app:latest your-docker-repo/weather-app:latest
    docker push your-docker-repo/weather-app:latest
    ```

## Jenkins

### Jenkinsfile Configuration

The `Jenkinsfile` automates the CI/CD pipeline. Here’s an outline of the steps:

1. **Clone the Repository**: Jenkins pulls the latest code from GitHub.
2. **Jenkins Stages**: Jenkins build , test and deploy project
3. **Deploy Docker Container**: Jenkins pulls the image from the Docker registry and creates a container from it.

### Setup Instructions for Jenkins

1. Ensure your Jenkins server has the following plugins installed:
   - **Git Plugin**: To clone the repository.
   - **Docker Pipeline Plugin**: To build and push Docker images.

2. Configure the Jenkins pipeline:
   - Create a new Jenkins pipeline job.
   - Use the `Jenkinsfile` from the repository for the pipeline configuration.
   - Build the job to start the process.

## Kubernetes

The `k8s` folder contains the necessary Kubernetes configuration files to deploy the Weather App.

### Deployment YAML

- `deployment.yaml`: Defines the pod specification and the desired number of replicas for the application.

### Service YAML

- `service.yaml`: Exposes the application as a service, allowing external access via a LoadBalancer or NodePort.

### Namespace YAML

- `namespace.yaml`: Defines the namespace where the application will run in the Kubernetes cluster.

### Kubernetes Deployment Commands

To deploy the Weather App to a Kubernetes cluster:

1. **Create the namespace**:
    ```bash
    kubectl apply -f k8s/namespace.yaml
    ```

2. **Deploy the application**:
    ```bash
    kubectl apply -f k8s/deployment.yaml
    ```

3. **Expose the service**:
    ```bash
    kubectl apply -f k8s/service.yaml
    ```

4. **Verify the pods and services are running**:
    ```bash
    kubectl get pods -n weather-app-namespace
    kubectl get services -n weather-app-namespace
    ```

