# FitPlanHub

A full-stack fitness platform where certified trainers create and sell fitness plans, and users subscribe to plans and follow trainers.

## Project Overview

FitPlanHub is a comprehensive fitness platform with:
- **Trainer capabilities**: Create, edit, and delete fitness plans
- **User capabilities**: Browse plans, subscribe, follow trainers, personalized feed
- **Authentication**: JWT-based authentication with role-based access control

## Tech Stack

### Backend
- **Framework**: FastAPI (Python)
- **Database**: PostgreSQL
- **ORM**: SQLAlchemy
- **Authentication**: JWT tokens with python-jose
- **Password Hashing**: bcrypt via passlib

### Frontend
- **Framework**: React.js with Vite
- **Routing**: React Router DOM
- **HTTP Client**: Axios
- **State Management**: React Context API
- **Notifications**: React Hot Toast

## Project Structure

```
/
├── backend/
│   ├── __init__.py
│   ├── config.py          # Configuration and environment variables
│   ├── database.py        # Database connection and session
│   ├── models.py          # SQLAlchemy models (User, FitnessPlan, Subscription, TrainerFollow)
│   ├── schemas.py         # Pydantic schemas for request/response
│   ├── auth.py            # Authentication utilities and middleware
│   └── routes/
│       ├── auth_routes.py     # /auth/signup, /auth/login, /auth/me
│       ├── trainer_routes.py  # Trainer CRUD for fitness plans
│       ├── plan_routes.py     # Public plan viewing and subscriptions
│       └── user_routes.py     # Follow/unfollow, feed, trainer profiles
├── client/
│   ├── src/
│   │   ├── components/    # Reusable React components
│   │   ├── context/       # AuthContext for state management
│   │   ├── pages/         # Page components
│   │   ├── services/      # API service with axios
│   │   ├── App.jsx        # Main app with routing
│   │   └── App.css        # Styles
│   └── vite.config.js     # Vite configuration
└── run.py                 # Backend entry point

```

## Database Models

### User
- id, name, email (unique), password_hash, role (trainer/user), created_at

### FitnessPlan
- id, title, description, price, duration_days, trainer_id (FK), created_at

### Subscription
- id, user_id (FK), plan_id (FK), subscribed_at

### TrainerFollow
- id, user_id (FK), trainer_id (FK), created_at

## API Endpoints

### Authentication
- `POST /auth/signup` - Register new user (trainer or user role)
- `POST /auth/login` - Login and get JWT token
- `GET /auth/me` - Get current user info

### Trainer (Trainer role only)
- `POST /trainer/plans` - Create new fitness plan
- `GET /trainer/plans` - Get trainer's own plans
- `PUT /trainer/plans/{id}` - Update a plan
- `DELETE /trainer/plans/{id}` - Delete a plan

### Plans (Public/User)
- `GET /plans` - List all plans (preview only)
- `GET /plans/{id}` - Get plan details (full if subscribed)
- `POST /plans/{id}/subscribe` - Subscribe to a plan

### Users
- `POST /trainers/{id}/follow` - Follow a trainer
- `DELETE /trainers/{id}/unfollow` - Unfollow a trainer
- `GET /users/me/following` - Get followed trainers
- `GET /users/me/feed` - Get personalized feed
- `GET /trainers/{id}` - Get trainer profile
- `GET /trainers` - List all trainers

## Running the Application

The application runs with two workflows:
1. **Backend API**: FastAPI server on port 5000
2. **Frontend**: React dev server on port 5173 with proxy to backend

## Access Control

- **Non-subscribed users**: See only title, trainer name, price
- **Subscribed users**: Full plan details including description
- **Trainers**: Can only modify their own plans

## Environment Variables

- `DATABASE_URL` - PostgreSQL connection string
- `SESSION_SECRET` - Secret key for JWT tokens
