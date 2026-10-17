# Project Expo Decentralized Voting System

A transparent, interactive voting and showcase platform for student innovation expos.

---

## Project Structure

```
Project-Expo-Voting-System/
│
├── react-app/              # Standalone Frontend (React + Vite + TailwindCSS + Framer Motion)
│   ├── src/
│   │   ├── components/     # UI components (Navbar, Hero, Leaderboard, ProjectCard, etc.)
│   │   ├── constants/      # Animation & category configurations
│   │   ├── context/        # ExpoContext state management
│   │   ├── data/           # Initial demo dataset
│   │   ├── pages/          # Home, Project Details, Vote, and Admin pages
│   │   └── styles/         # Glassmorphism & neon theme styling
│   ├── package.json
│   └── vite.config.js
│
├── backend/                # Standalone Backend (Node.js + Express + MongoDB + JWT)
│   ├── config/
│   │   └── db.js           # Local MongoDB Mongoose connection
│   ├── controllers/        # Route controllers (Auth, Projects, Votes, Feedback, Results)
│   ├── middleware/         # JWT Auth & Admin authorization middlewares
│   ├── models/             # Mongoose schemas (User, Project, Vote, Feedback)
│   ├── routes/             # API routing endpoints
│   ├── server.js           # Express application entry point
│   ├── seed.js             # Initial database seeder script
│   ├── package.json
│   └── .env
│
└── README.md
```

---

## Getting Started

### 1. Frontend (React Application)

```bash
cd react-app
npm install
npm run dev
```

* Frontend runs on `http://localhost:3000` (or Vite's assigned port).

---

### 2. Backend (Node.js + Express + MongoDB)

Make sure local MongoDB is running (`mongodb://localhost:27017/decentralized_voting`).

```bash
cd backend
npm install
npm run seed     # (Optional) Seed initial users and projects
npm run dev      # Start development server with nodemon
```

* Backend runs on `http://localhost:5000`.
* Health check: `http://localhost:5000/api/health`.

---

## API Summary

| Feature | Method | Endpoint | Protection |
| :--- | :--- | :--- | :--- |
| **Health** | `GET` | `/api/health` | Public |
| **Register** | `POST` | `/api/auth/register` | Public |
| **Login** | `POST` | `/api/auth/login` | Public |
| **Get Projects** | `GET` | `/api/projects` | Public |
| **Get Project** | `GET` | `/api/projects/:id` | Public |
| **Create Project** | `POST` | `/api/projects` | Admin (JWT) |
| **Update Project** | `PUT` | `/api/projects/:id` | Admin (JWT) |
| **Delete Project** | `DELETE` | `/api/projects/:id` | Admin (JWT) |
| **Cast Vote** | `POST` | `/api/votes` | User (JWT, 1-vote/project) |
| **Check Voted** | `GET` | `/api/votes/check/:projectId` | User (JWT) |
| **Submit Feedback** | `POST` | `/api/feedback` | User (JWT) |
| **Get Feedback** | `GET` | `/api/feedback/:projectId` | Public |
| **Leaderboard / Results** | `GET` | `/api/results` | Public |
| **Project Results** | `GET` | `/api/results/:projectId` | Public |
