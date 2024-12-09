## Project Structure
```
.
├── cosmocloud-deploy
│   ├── Charts.yml
│   ├── values.yml
|  
├── templates
|       └── backend-deployment.yml
│       └── backend-service.yml
|       └── frontend-deployment.yml
│       └── frontend-service.yml
|       └── redis-deployment.yml
|       └── redis-service.yml
|   
├── Readme
│   
.
```

# cosmocloud-deploy
Cosmocloud-Deploy is a Helm chart designed to deploy a backend, frontend, and Redis for a cloud-native application. This project simplifies the deployment of these components using Kubernetes.

Helm Chart Details
Chart Name: cosmocloud-deploy
Chart Version: 1.0.0
App Version: 1.0.0
Type: Application

## values.yaml
- The values.yaml file is the configuration file used to customize the deployment of the Cosmocloud-Deploy Helm chart. This file contains all the configurable parameters for the backend, frontend, and Redis components, allowing users to easily adjust the deployment without modifying the chart templates.

### Key Sections in values.yaml:
#### Global Settings:

- replicaCount: Number of replicas for each deployment.
- namespace: The namespace in which the resources will be deployed.
##### Backend Configuration:

- backend.image: The Docker image for the backend application.
- backend.servicePort: The port exposed by the backend service.
##### Frontend Configuration:

- frontend.image: The Docker image for the frontend application.
- frontend.servicePort: The port exposed by the frontend service.
- frontend.nodePort: The NodePort to access the frontend application externally.

##### Redis Configuration:

- redis.image: The Docker image for the Redis database.
- redis.servicePort: The port exposed by the Redis service.
## Components Deployed:
Backend
Frontend
Redis
### Deployment Structure
#### 1. Backend
- Deployment File: backend-deployment.yml( name: backend-deployment, app: backend-app)
- Service File: backend-service.yml( name: backend-svc)
- ConfigMap: Holds REDIS_URI for backend communication with Redis.
##### Key Details:

- Image: shreybatra/sample-backend
- Port: 8000
- Environment Variable:
- REDIS_URI: redis://redis-svc:6379
#### 2. Frontend
- Deployment File: frontend-deployment.yml( name: frontend-deployment, app: frontend-app)
- Service File: frontend-service.yml( name: frontend-svc)
- ConfigMap: Holds BACKEND_URL for frontend communication with the backend.
##### Key Details:

- Image: shreybatra/sample-frontend
- Port: 5173
- NodePort: 31000
- Environment Variable:
- BACKEND_URL: http://backend-svc:8000
#### 3. Redis
- Deployment File: redis-deployment.yml( name: redis-deployment, app: redis-app)
- Service File: redis-service.yml( name: redis-svc)
##### Key Details:

- Image: redis
- Port: 6379
- ---------------------------------------
- git clone: https://github.com/chakri592/cosmocloud-deploy.git
