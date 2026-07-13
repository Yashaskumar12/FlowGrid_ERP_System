# Deployment Guide

This document covers local development, Docker-based setup, and AWS EC2 deployment for FlowGrid ERP.

## Local Development

### Frontend

```bash
npm install
npm run dev
```

### Backend

```bash
cd server
npm install
npm run dev
```

### Full stack with Docker

```bash
docker compose up --build
```

## Environment Variables

### Root frontend

```env
VITE_API_URL=http://localhost:5000/api
```

### Backend

```env
MONGODB_URI=mongodb://admin:password@localhost:27017/flowgrid?authSource=admin
JWT_SECRET=change-me
PORT=5000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
```

## AWS EC2 Deployment

1. Provision an EC2 instance.
2. Install Docker and Docker Compose.
3. Clone the repository.
4. Copy the production environment template.
5. Run the deployment script.

```bash
chmod +x scripts/deploy.sh
./scripts/deploy.sh
```

## Verification

```bash
./deploy/test-deployment.sh
```

## Troubleshooting

- Check the API health endpoint: `http://your-server:5000/health`
- Review Docker logs: `docker compose logs -f`
- Ensure MongoDB is reachable from the backend container
- Confirm the frontend `VITE_API_URL` points to the correct backend host
