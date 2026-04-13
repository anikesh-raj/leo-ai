<div align="center">

<br/>

```
██╗     ███████╗ ██████╗
██║     ██╔════╝██╔═══██╗
██║     █████╗  ██║   ██║
██║     ██╔══╝  ██║   ██║
███████╗███████╗╚██████╔╝
╚══════╝╚══════╝ ╚═════╝
```

### The Autonomous Neural OS Agent

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" />
</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-features">Features</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-project-structure">Structure</a> •
  <a href="#-setup">Setup</a> •
  <a href="#-deployment">Deployment</a>
</p>

<br/>

> **LEO** is not a chatbot. It is a **local-first AI Operating System layer** — turn your voice into real OS-level actions across your system, apps, and devices.

<br/>

</div>

---

## ⚡ Overview

LEO is a **full-stack web platform** for the LEO AI Desktop Engine — a voice-driven autonomous agent that executes real-world commands across your operating system.

This repository contains **two deployable projects**:

| Project | Tech | Purpose |
|---|---|---|
| `client/` | Next.js 15 + Tailwind | Landing page, auth, pricing, download |
| `server/` | Node.js + Express + MongoDB | Auth API, JWT, Google OAuth |

The actual desktop AI engine (Electron app) is a separate repository.

---

## ✨ Features

### 🌐 Web Platform
- **Landing Page** — Animated hero, features showcase, tech stack ticker
- **Authentication** — JWT-based login/signup + Google OAuth 2.0
- **Email Verification** — Token-based account verification flow
- **Pricing Page** — Free vs Pro tier comparison
- **Download Page** — Desktop app distribution
- **Guide Page** — API key setup walkthrough
- **Features Page** — Full capability showcase

### 🔐 Backend API
- **JWT Authentication** — Access + Refresh token rotation
- **Google OAuth 2.0** — Passport.js strategy
- **MongoDB** — User model with Mongoose
- **Cookie-based Sessions** — Secure httpOnly refresh tokens
- **Rate Limiting** — API abuse protection

---

## 🛠️ Tech Stack

### Frontend — `client/`
| Tech | Version | Use |
|---|---|---|
| Next.js | 15 | React framework + SSR |
| TypeScript | 5 | Type safety |
| Tailwind CSS | 4 | Styling |
| Framer Motion | — | Animations |
| Axios | — | HTTP client |
| GSAP | — | Advanced animations |
| Lucide React | — | Icons |

### Backend — `server/`
| Tech | Version | Use |
|---|---|---|
| Node.js | 20+ | Runtime |
| Express | — | HTTP server |
| TypeScript | 5 | Type safety |
| MongoDB + Mongoose | — | Database |
| JWT | — | Auth tokens |
| Passport.js | — | Google OAuth |
| Bcrypt | — | Password hashing |
| tsx | — | TS dev runner |

---

## 📁 Project Structure

```
leo-Web-main/
│
├── client/                        # Next.js Frontend
│   ├── app/
│   │   ├── Components/            # Header, Footer, ScratchCard
│   │   ├── Landing/               # Main landing page component
│   │   ├── about/                 # About page
│   │   ├── features/              # Features showcase
│   │   ├── pricing/               # Pricing tiers
│   │   ├── download/              # Desktop app download
│   │   ├── guide/                 # Setup guide
│   │   ├── login/                 # Login page
│   │   ├── signup/                # Signup page
│   │   ├── verify/                # Email verification
│   │   ├── desktop/               # Desktop app redirect
│   │   ├── utils/                 # Animated UI components
│   │   ├── layout.tsx             # Root layout + metadata
│   │   └── page.tsx               # Home route
│   ├── config/
│   │   └── AxiosInstance.ts       # Axios base config
│   ├── public/
│   │   ├── img/                   # Images & logos
│   │   ├── fonts/                 # Custom fonts
│   │   └── videos/                # Pre-load video
│   ├── .env.local                 # ← Create this (see Setup)
│   └── package.json
│
├── server/                        # Express Backend
│   ├── src/
│   │   ├── controllers/           # Route handlers
│   │   ├── models/                # Mongoose schemas
│   │   ├── routes/                # API routes
│   │   ├── middlewares/           # Auth, rate limiting
│   │   ├── services/              # Business logic
│   │   ├── lib/                   # Passport config
│   │   ├── utils/                 # JWT, cookie helpers
│   │   ├── database/              # MongoDB connection
│   │   ├── config/                # App config
│   │   ├── app.ts                 # Express app setup
│   │   └── index.ts               # Server entry point
│   ├── .env                       # ← Create this (see Setup)
│   └── package.json
│
└── .env.example                   # Reference template
```

---

## 🚀 Setup

### Prerequisites

- Node.js v20+
- MongoDB Atlas account (free tier works)
- Google Cloud Console project (for OAuth)

---

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/leo-Web.git
cd leo-Web
```

---

### 2. Server setup

```bash
cd server
npm install
```

Create `server/.env`:

```env
# Server
PORT=4000

# MongoDB Atlas connection string
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/LEO-AI?retryWrites=true&w=majority&appName=Cluster0

# Client URL (for CORS)
CLIENT_URL=http://localhost:3000

# JWT Secrets — generate with: node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
ACCESS_TOKEN_SECRET=your_strong_random_secret_here
REFRESH_TOKEN_SECRET=your_different_strong_random_secret_here

# Token expiry
ACCESS_TOKEN_EXPIRY=15m
REFRESH_TOKEN_EXPIRY=30d

# Google OAuth — from Google Cloud Console
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
```

Start the server:

```bash
npm run dev
```

Server runs on `http://localhost:4000`

---

### 3. Client setup

```bash
cd client
npm install
```

Create `client/.env.local`:

```env
NEXT_PUBLIC_SERVER_URL=http://localhost:4000
```

Start the client:

```bash
npm run dev
```

Client runs on `http://localhost:3000`

---

## 🔑 Getting API Keys

### MongoDB Atlas
1. Go to [cloud.mongodb.com](https://cloud.mongodb.com)
2. Create a free cluster
3. Database Access → Add user with password
4. Network Access → Add `0.0.0.0/0` (allow all IPs)
5. Connect → Drivers → Copy connection string

### Google OAuth
1. Go to [console.cloud.google.com](https://console.cloud.google.com)
2. Create project → APIs & Services → Credentials
3. Create OAuth 2.0 Client ID → Web application
4. Add Authorized JavaScript Origins:
   - `http://localhost:3000`
   - `http://localhost:4000`
5. Add Authorized Redirect URIs:
   - `http://localhost:4000/users/google/callback`
6. Copy Client ID and Client Secret

### JWT Secrets
Generate secure random secrets:
```bash
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```
Run twice — use one for `ACCESS_TOKEN_SECRET`, another for `REFRESH_TOKEN_SECRET`.

---

## 🌍 Deployment

This project deploys as **2 separate Vercel projects** from the same repo.

### Deploy Backend (server/)

1. Push repo to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project → Import repo
3. Set **Root Directory** → `server`
4. Add all environment variables from `server/.env`
5. Set `CLIENT_URL` to your frontend Vercel URL (add after frontend deploy)
6. Deploy → copy the backend URL

### Deploy Frontend (client/)

1. New Project → same GitHub repo
2. Set **Root Directory** → `client`
3. Add environment variable:
   ```
   NEXT_PUBLIC_SERVER_URL=https://your-backend.vercel.app
   ```
4. Deploy → copy the frontend URL

### Post-deploy

- Update `CLIENT_URL` in backend env to frontend URL → Redeploy backend
- Add Vercel URLs to Google Cloud Console OAuth settings:
  - Authorized Origins: `https://your-frontend.vercel.app`, `https://your-backend.vercel.app`
  - Redirect URI: `https://your-backend.vercel.app/users/google/callback`

---

## 🔗 API Routes

```
POST   /users/register              Register new user
POST   /users/login                 Login with email/password
POST   /users/logout                Logout (clears cookie)
GET    /users/me                    Get current user (auth required)
GET    /users/google                Initiate Google OAuth
GET    /users/google/callback       Google OAuth callback
POST   /users/verify                Verify email token
POST   /users/refresh-token         Refresh access token
```

---

## ⚠️ Important Notes

- Never commit `.env` or `.env.local` files — they are gitignored
- Keep `ACCESS_TOKEN_SECRET` and `REFRESH_TOKEN_SECRET` different from each other
- MongoDB Atlas free tier (M0) is sufficient for development and small production workloads
- The desktop AI engine (Electron app) is a **separate project** — this repo is only the web platform

---

## 📜 License

MIT License — see [LICENSE](LICENSE) file.

---

<div align="center">

**LEO** — Turn intent into execution.

Made with ❤️ by [Your Name](https://github.com/anikesh-raj)

</div>
