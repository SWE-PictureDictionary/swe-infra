SWE Microservices Project

This project is a distributed microservices system built with Spring Boot, Docker, and Kubernetes. Each service is maintained in its own repository and deployed together using Kubernetes.

Repositories

Each service is separated into its own GitHub repository:

UI:
https://github.com/sinedon/swe-ui

Edge Service (API Gateway):
https://github.com/sinedon/swe-edge-service

Config Repo:
https://github.com/sinedon/swe-config-repo

Config Service:
https://github.com/sinedon/swe-config-service

Content Access:
https://github.com/sinedon/swe-content-access

Content Manager:
https://github.com/sinedon/swe-content-manager

Event Processor:
https://github.com/sinedon/swe-event-processor

Progress Access:
https://github.com/sinedon/swe-progress-access

Progress Manager:
https://github.com/sinedon/swe-progress-manager

Completion Engine:
https://github.com/sinedon/swe-completion-engine

Kubernetes Infrastructure:
https://github.com/sinedon/swe-infra

Running the Project (Kubernetes)

Clone the infrastructure repository

git clone https://github.com/sinedon/swe-infra

cd swe-infra

Deploy all services

kubectl apply -f .

Restart deployments (ensures latest images are used)

kubectl rollout restart deployment

Check pod status

kubectl get pods

Wait until all pods show "Running".

Access the application

kubectl port-forward svc/ui 8000:80

Then open in your browser:

http://localhost:8000/

Development Workflow

Each service is developed in its own repository
Make changes in the appropriate service repository
You can test locally using Docker Compose if needed
After making changes:
Verify the service works locally
Push changes to the corresponding repository
Confirm everything still works in Kubernetes

Notes

Kubernetes does NOT automatically update running containers when images change
You must restart deployments to pull the latest images
All services communicate through the edge-service (API gateway)
Configuration is handled via config-service and config-repo
