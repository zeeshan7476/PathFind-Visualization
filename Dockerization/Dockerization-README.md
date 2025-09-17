# 🚀 Project Setup with Docker

This project contains three main components:

- **Backend** → Node.js + Express (Port: `5000`)  
- **Frontend** → Vite + Node.js (Port: `5173`)  
- **Database** → MongoDB (Port: `27017`)  

All services are containerized using **Docker** for easy setup and deployment.  

---

## 📌 Prerequisites

- Install [Docker](https://www.docker.com/get-started) and ensure it is running.

---

## 🗄️ Database (MongoDB)

Run MongoDB in a Docker container:

```bash
sudo docker run -d -p 27017:27017 --name mongo mongo:latest
```

This will:  
- Pull the latest MongoDB image  
- Run it in detached mode  
- Map port `27017` to your host machine  

You can connect to MongoDB at:

```
mongodb://localhost:27017
```

👉 Make sure your backend `.env` file points to this URI.  

---

## ⚙️ Backend Setup

### Dockerfile

```dockerfile
FROM node:21
WORKDIR /app
COPY . .
RUN npm i
COPY .env.sample .env
EXPOSE 5000
CMD ["npm", "start"]
```

### Build & Run

```bash
# Build backend image
docker build -t backend .

# Run backend container
docker run -d -p 5000:5000 --name backend backend
```

Backend available at:  
👉 [http://localhost:5000](http://localhost:5000)

---

## 🎨 Frontend Setup

### Dockerfile

```dockerfile
FROM node:21

WORKDIR /app

COPY package*.json ./

# Install dependencies (skip lifecycle scripts like husky)
RUN npm install --ignore-scripts

COPY . .

COPY .env.sample .env.local

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]

```

### Build & Run

```bash
# Build frontend image
docker build -t frontend .

# Run frontend container
docker run -d -p 5173:5173 --name frontend frontend
```

Frontend available at:  
👉 [http://localhost:5173](http://localhost:5173)

---

## 🌍 Environment Variables

- **Backend** → Copies `.env.sample` to `.env` during build.  
- **Frontend** → Copies `.env.sample` to `.env.local` during build.  

⚠️ Update your `.env.sample` files with correct values **before** building images.  

---

## 🛑 Stopping Containers

To stop and remove running containers:

```bash
docker stop backend frontend mongo
docker rm backend frontend mongo
```

---

✅ You now have a full setup for **Backend + Frontend + MongoDB** with Docker!
