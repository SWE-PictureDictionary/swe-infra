SWE Microservices Project

This project is a distributed microservices system built with Spring Boot, Docker, and Kubernetes. Each service is maintained in its own repository under a shared GitHub organization and deployed together using Kubernetes.

Organization

All repositories are now managed under the GitHub organization:

SWE-PictureDictionary

Repositories

Each service is separated into its own repository within the organization:

UI
https://github.com/SWE-PictureDictionary/swe-ui

Edge Service (API Gateway)
https://github.com/SWE-PictureDictionary/swe-edge-service

Config Repository
https://github.com/SWE-PictureDictionary/swe-config-repo

Config Service
https://github.com/SWE-PictureDictionary/swe-config-service

Content Access
https://github.com/SWE-PictureDictionary/swe-content-access

Content Manager
https://github.com/SWE-PictureDictionary/swe-content-manager

Event Processor
https://github.com/SWE-PictureDictionary/swe-event-processor

Progress Access
https://github.com/SWE-PictureDictionary/swe-progress-access

Progress Manager
https://github.com/SWE-PictureDictionary/swe-progress-manager

Completion Engine
https://github.com/SWE-PictureDictionary/swe-completion-engine

Kubernetes Infrastructure
https://github.com/SWE-PictureDictionary/swe-infra

Running the Project (Kubernetes)
1. Clone the infrastructure repository
git clone https://github.com/SWE-PictureDictionary/swe-infra
cd swe-infra

2. Deploy all services
kubectl apply -f .

3. Restart deployments (pull latest images)
kubectl rollout restart deployment

4. Check pod status
kubectl get pods


Wait until all pods show Running.

5. Access the application
kubectl port-forward svc/ui 8000:80


Then open in your browser:

http://localhost:8000/

Development Workflow

Each microservice is developed in its own repository within the organization

Clone and work within the specific service you want to modify

Test locally (Docker or Docker Compose recommended)

After making changes:

Verify the service works locally

Push changes to the corresponding repository in the organization

Ensure CI/CD workflows pass (if configured)

Restart Kubernetes deployments to pull updated images

Configuration

Configuration is handled through:

Config Repository
https://github.com/SWE-PictureDictionary/swe-config-repo

Config Service
https://github.com/SWE-PictureDictionary/swe-config-service

These provide centralized configuration management for all services.

Notes

Kubernetes does not automatically update running containers when images change

You must restart deployments to pull the latest images

All services communicate through the edge-service (API gateway)
