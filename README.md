# 🏋️ FitPlanHub – Trainers & Users Fitness Platform

FitPlanHub is a full-stack fitness platform where certified trainers create paid fitness plans and users can subscribe, follow trainers, and access personalized fitness content.

The project demonstrates real-world backend architecture, JWT authentication, role-based access control, and a modern React frontend integrated with a FastAPI backend.

# 🚀 Features Overview
## 🔐 Authentication & Authorization

User and Trainer signup & login

Secure password hashing using bcrypt

JWT-based authentication

Role-based access (USER, TRAINER)

## 🧑‍🏫 Trainer Capabilities

Create, update, delete fitness plans

View all plans they created

See subscribed users (optional extension)

Dedicated Trainer Dashboard UI

## 🧑‍💻 User Capabilities

Browse all available fitness plans

Preview plans before subscribing

Subscribe to fitness plans (simulated payment)

Follow / unfollow trainers

Personalized feed from followed trainers

Dedicated User Dashboard UI

## 🔒 Access Control Rules

Non-subscribed users see preview only

Subscribed users get full plan details

Trainers cannot subscribe to their own plans

Duplicate subscriptions are prevented

## 🧱 Tech Stack
Backend

FastAPI – REST API framework

PostgreSQL – Relational database

SQLAlchemy – ORM

Pydantic v2 – Data validation

JWT (python-jose) – Authentication

Passlib + bcrypt – Password hashing

Pytest – Automated testing

Frontend

React.js + vite – UI framework

Axios – API communication

Context API – Global auth state

Role-based UI rendering

Clean, minimal, responsive design


## ⚙️ Backend Setup Instructions
### 1️⃣ Create Virtual Environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

### 2️⃣ Install Dependencies
pip install -r requirements.txt

### 3️⃣ Configure .env
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/fitplanhub_db
SECRET_KEY=your_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=60

### 4️⃣ Run Backend
uvicorn main:app --reload

### 5️⃣ API Docs
http://localhost:8000/docs

## ⚙️ Frontend Setup Instructions
### 1️⃣ Install Dependencies
npm install

### 2️⃣ Run Frontend
npm run dev


Frontend runs on:

http://localhost:3000

## 🔑 Authentication Flow (Important)

User logs in → receives JWT access token

Token stored in localStorage

Frontend calls:

GET /auth/me


App sets global auth state

UI updates automatically based on role

## 🔐 Key API Endpoints
Auth
Method	Endpoint	Description
POST	/auth/signup	Register user/trainer
POST	/auth/login	Login & get token
GET	/auth/me	Get logged-in user
Plans
Method	Endpoint
GET	/plans
POST	/trainer/plans
PUT	/trainer/plans/{id}
DELETE	/trainer/plans/{id}
Subscriptions

| POST | /subscriptions/{plan_id} |

Follow Trainers

| POST | /trainers/{trainer_id}/follow |


## 🧠 Learning Outcomes

This project demonstrates:

Real-world JWT authentication

Role-based authorization

Clean API design

Secure password handling

Frontend–backend integration

Scalable project structure

## 📌 Future Enhancements

Real payment gateway integration

Admin dashboard

Analytics & reports

Notifications

Mobile app (React Native)

## 👨‍💻 Author

Tarun Patidar
B.Tech CSE | Full-Stack Developer
Focused on backend architecture, APIs, and scalable systems.
