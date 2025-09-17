# PathFind-Visualization

PathFind-Visualization is a full-stack application that demonstrates seamless integration of a **Node.js + MongoDB backend** with a **React frontend**.  
The project allows developers to quickly set up a scalable development environment and learn modern application architecture practices.

---

## 📌 Project Architecture

The project follows a **three-tier architecture**:

```
   ┌───────────────────┐
   │     Frontend      │
   │  (React + Vite)   │
   └────────┬──────────┘
            │
            ▼
   ┌───────────────────┐
   │     Backend       │
   │ (Node.js + NPM)   │
   └────────┬──────────┘
            │
            ▼
   ┌───────────────────┐
   │   Database Layer  │
   │   (MongoDB 8.0)   │
   └───────────────────┘
```

- **Frontend**: React handles the user interface.  
- **Backend**: Node.js (Express) manages the API and business logic.  
- **Database**: MongoDB stores application data.  

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/{your-username}/PathFind.git
cd PathFind-Visualization
```

---

## ⚙️ Backend Setup

### Step 1: Navigate to Backend Directory
```bash
cd backend
```

### Step 2: Install Node.js & NPM using NVM
```bash
# Install NVM (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Reboot your system if 'nvm' command not found
sudo reboot

# Install Node.js version 21
nvm install 21

# Verify installations
node -v   # should print v21.7.2
npm -v    # should print 10.5.0
```

### Step 3: Install Dependencies
```bash
npm i
```

### Step 4: Set Up MongoDB

#### (a) Import the MongoDB GPG Key
```bash
sudo apt-get install gnupg curl
curl -fsSL https://www.mongodb.org/static/pgp/server-8.0.asc |    sudo gpg -o /usr/share/keyrings/mongodb-server-8.0.gpg --dearmor
```

#### (b) Create the MongoDB List File
```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-8.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/8.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-8.0.list
```

#### (c) Reload & Install MongoDB
```bash
sudo apt-get update
sudo apt-get install -y mongodb-org
```

#### (d) Start MongoDB
```bash
sudo systemctl start mongod
```

> ✅ You can connect using MongoDB Compass at:  
> `mongodb://localhost:27017`

---

### Step 5: Import Sample Data
```bash
mongoimport --db pathfind --collection posts --file ./data/sample_posts.json --jsonArray
```
Or, if you want to drop existing data before importing:
```bash
mongoimport --db pathfind --collection posts --file ./data/sample_posts.json --jsonArray --drop
```

---

### Step 6: Configure Environment Variables
```bash
cp .env.sample .env
```

---

### Step 7: Start the Backend Server
```bash
npm start
```

---

## 🎨 Frontend Setup

### Step 1: Open a New Terminal & Navigate to Frontend
```bash
cd frontend
```

### Step 2: Install Dependencies
```bash
npm i
```

### Step 3: Configure Environment Variables
```bash
cp .env.sample .env.local
```

### Step 4: Launch Development Server
```bash
npm run dev
```

---

## ✅ Summary

- **Backend**: Node.js + MongoDB  
- **Frontend**: React  
- **Database**: MongoDB Community Server  
- **Sample Data**: `posts` collection in `pathfind` database  
- **Default MongoDB URI**: `mongodb://localhost:27017`  

This project provides a practical, hands-on setup for modern full-stack development.

---
