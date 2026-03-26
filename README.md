# Lab 10 – AI Enhanced Group Chat (Web + Android)

This project implements a full-stack AI-enhanced group chat system, including:

- Backend: FastAPI + MySQL
- Frontend: HTML/CSS/JavaScript
- LLM integration (optional)
- Android wrapper using Trusted Web Activity (TWA)

---

# 📦 Project Structure



---

# 🚀 Part 1 – Web Application Setup

## 1. Prerequisites

- Python 3.10+
- MySQL 8+
- pip

---

## 2. Database Setup

Login to MySQL and run:


CREATE DATABASE groupchat CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

CREATE USER 'chatuser'@'localhost' IDENTIFIED BY 'chatpass';

GRANT ALL PRIVILEGES ON groupchat.* TO 'chatuser'@'localhost';

FLUSH PRIVILEGES;


---

## 3. Backend Setup

cd groupchat_app_src/backend

python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

pip install -r requirements.txt

## 4. Environment Configuration

cp ../.env.example ../.env
DATABASE_URL=mysql+asyncmy://chatuser:chatpass@localhost:3306/groupchat

JWT_SECRET=your_secret_here
JWT_EXPIRE_MINUTES=43200

LLM_API_BASE=http://localhost:8001/v1
LLM_MODEL=llama-3-8b-instruct
LLM_API_KEY=

APP_HOST=0.0.0.0
APP_PORT=8000

-----

## 5. Run Backend
uvicorn app:app --host 0.0.0.0 --port 8000

Open browser:

http://localhost:8000
----
## 6. Test Web App
Sign up
Log in
Send messages
Messages containing ? trigger LLM (if configured)

(Optional) LLM Setup

You can run a local Llama model:

./llama-server -m /path/to/model.gguf --host 0.0.0.0 --port 8001

Then ensure .env:

LLM_API_BASE=http://localhost:8001/v1

