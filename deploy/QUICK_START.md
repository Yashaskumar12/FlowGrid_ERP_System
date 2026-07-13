# Quick Start Guide

This guide helps you get FlowGrid ERP running locally or deploy it to AWS EC2 quickly.

## 1. Prerequisites

- Node.js 20+
- npm 10+
- Docker Desktop or Docker Engine
- MongoDB (or Docker Compose)

## 2. Local Development

### Install dependencies

```bash
npm install
cd server && npm install && cd ..
```

### Start MongoDB

```bash
docker compose up mongodb -d
```

### Start backend

```bash
cd server
npm run dev
```

### Start frontend

```bash
cd ..
npm run dev
```

Open http://localhost:5173

## 3. Environment Variables

Create a frontend `.env` file:

```env
VITE_API_URL=http://localhost:5000/api
```

Create `server/.env`:

```env
MONGODB_URI=mongodb://admin:password@localhost:27017/flowgrid?authSource=admin
JWT_SECRET=your-secret-key
PORT=5000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
```

## 4. Deploy to EC2

Run the EC2 setup script:

```bash
chmod +x deploy/setup-ec2.sh
./deploy/setup-ec2.sh
```

Then verify the deployment:

```bash
./deploy/test-deployment.sh
```

## 5. Troubleshooting

- Check containers with `docker compose ps`
- Inspect logs with `docker compose logs -f`
- Restart services with `docker compose restart`
- If the API is not reachable, verify the backend port and MongoDB connection string
