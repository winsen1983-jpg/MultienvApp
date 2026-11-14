# Multi-Environment Ticket Management Application Deployment
Screenshots are saved in the Evidence Folder for reference.

A containerized multi-environment full-stack ticket management system featuring a **React Frontend** (Nginx) and dual **Python Flask Backends** (**Development** & **Production**) connected to **MongoDB Atlas**.

## 1. Architecture & Specifications
* **Environment:** Windows / Docker Desktop (WSL2)
* **Orchestration:** Docker Compose (v2+)
* **Network:** Custom Bridge Network (multienvapp_multienv-network / 172.24.0.0/16)
* **Database:** MongoDB Atlas (tickets_dev & tickets_prod)

## 2. Prerequisites & Quick Start
* **Prerequisites:** Docker Desktop (v24.0+), Git, MongoDB Atlas URI.
* **Clone & Configure:**
  1. Clone: git clone (https://github.com/winsen1983-jpg/MultienvApp)
  2. Create .env files in backend/dev/ (PORT=3001, MONGO_URI, FLASK_ENV=development) and backend/prod/ (PORT=3002, MONGO_URI, FLASK_ENV=production).
* **Build & Verify:**
  - Start: docker compose up --build -d
  - Check status: docker ps
  - View logs: docker compose logs --tail=20

## 3. Access URLs & Port Mapping
| Service | Container Name | Port | Access URL |
| :--- | :--- | :--- | :--- |
| React Frontend (Nginx) | ticket-frontend | 3000 | http://localhost:3000 |
| Dev UI / Prod UI | ticket-frontend | 3000 | http://localhost:3000/dev & /prod |
| Flask Dev API | ticket-backend-dev | 3001 | http://localhost:3001 |
| Flask Prod API | ticket-backend-prod | 3002 | http://localhost:3002 |

## 4. Key Design Choices & Troubleshooting
* **Frontend Optimization:** Multi-stage build using node:18-alpine to nginx:alpine with SPA try_files routing.
* **Database Driver:** Installed dnspython in Flask requirements to support mongodb+srv:// connections.
* **Build Fixes:** Disabled ESLint plugin in React Dockerfile (DISABLE_ESLINT_PLUGIN=true) and encoded files in BOM-free UTF-8.

## 5. Testing Evidence (Screenshots in evidence/)
* docker-ps.png: Running containers check
* docker-logs.png: Service logs verification
* network-inspect.png: Custom bridge network inspection
* frontend-home.png, frontend-dev.png, frontend-prod.png: UI dashboards
