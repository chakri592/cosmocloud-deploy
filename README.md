

# cosmocloud-deploy
Cosmocloud-Deploy is a Helm chart designed to deploy a backend, frontend, and Redis for a cloud-native application. This project simplifies the deployment of these components using Kubernetes.

Helm Chart Details
Chart Name: cosmocloud-deploy
Chart Version: 1.0.0
App Version: 1.0.0
Type: Application
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
