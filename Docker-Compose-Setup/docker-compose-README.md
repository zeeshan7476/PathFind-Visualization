# 🚀 Full-Stack Application with Docker Compose

This project sets up a **MERN stack (MongoDB, Express.js, React, Node.js)** using Docker Compose for easy development and deployment.

---

## 📦 Project Structure
```
.
├── backend/         # Node.js + Express server
│   ├── Dockerfile
│   └── .env.sample
├── frontend/        # React application
│   └── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## ⚙️ Services

### 1. MongoDB
- Runs the latest MongoDB container.
- Data persisted in `./backend/data` → `/data/db` inside the container.
- Exposed on **port 27017**.

### 2. Backend (Node.js / Express)
- Built from the `backend/` directory.
- Loads environment variables from `.env.sample`.
- Exposed on **port 5000**.
- Depends on MongoDB service.

### 3. Frontend (React)
- Built from the `frontend/` directory.
- Uses environment variables from `.env.sample`.
- Exposed on **port 5173**.
- Depends on the Backend service.

---

## ▶️ Usage

### Start the stack
```bash
docker-compose up --build
```

### Stop the stack
```bash
docker-compose down
```

### Remove all containers & volumes
```bash
docker-compose down -v
```

---

## 🌐 Access
- Frontend → [http://localhost:5173](http://localhost:5173)  
- Backend → [http://localhost:5000](http://localhost:5000)  
- MongoDB → `mongodb://localhost:27017`  

---

## 📝 Notes
- Update `.env.sample` with your own environment variables.  
- Modify ports in `docker-compose.yml` if they conflict with your local setup.  
- Data is stored persistently in the `backend/data` directory.  
