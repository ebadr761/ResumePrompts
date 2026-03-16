# FightMetrics — MMA Tracker Prompts

Reusable prompts for generating resume bullet points for different internship roles based on the **FightMetrics full-stack project**.

---

# Table of Contents

1. [Software Engineering Intern](#software-engineering-intern)
2. [Machine Learning / Data Science Intern](#machine-learning--data-science-intern)
3. [DevOps / Infrastructure / Platform Intern](#devops--infrastructure--platform-intern)
4. [Frontend / UI Engineering Intern](#frontend--ui-engineering-intern)
5. [General / Catch-All SWE Intern](#general--catch-all-swe-intern)

---

# Software Engineering Intern

```text
I need 4–5 resume bullet points for a project called "FightMetrics (MMA Tracker)" for a Software Engineering Intern role. Use the STAR/XYZ format (action verb + what you did + tech + impact). Make them concise, quantifiable, and ATS-friendly.

Here are the verified technical facts from the codebase. Do NOT invent metrics — only use what's given:

PROJECT OVERVIEW:
- Full-stack athletic performance tracking platform with AI-powered training insights for combat sports athletes
- Solo-developed (personal project)

BACKEND (Python):
- Built a RESTful API with FastAPI (async) serving 8 endpoints across 3 route modules (auth, workouts, ML)
- Async MongoDB integration via Motor driver with TLS certificate pinning (certifi)
- Full CRUD operations on workouts with MongoDB aggregation pipelines for real-time stats (total sessions, duration, avg intensity)
- Pydantic v2 data models with strict validation (Literal types for 8 discipline categories, Field constraints ge/le)
- JWT-based stateless authentication using python-jose + bcrypt password hashing via passlib
- Application lifecycle management with FastAPI's asynccontextmanager (startup/shutdown DB connections)
- Configurable CORS middleware with environment-based origin whitelisting

FRONTEND (React/TypeScript):
- React 18 + TypeScript + Vite build system
- Modular component architecture: Dashboard decomposed into 5 sub-components (StatsOverview, InsightsWidget, WorkoutForm, WorkoutHistory, WorkoutCharts)
- Interactive data visualizations using Recharts (discipline breakdown bar charts, 7-day training timeline)
- Axios HTTP client with request/response interceptors for automatic JWT injection and 401 redirect handling
- React Context API for global auth state management with persistent session via localStorage
- Dark/light theme toggle with CSS variable theming and localStorage persistence
- Toast notification system with auto-dismiss
- TailwindCSS for responsive, utility-first styling

MACHINE LEARNING ENGINE (Scikit-Learn):
- K-Means clustering (n=3 clusters) on duration × intensity features to identify training pattern ruts
- Acute:Chronic Workload Ratio (ACWR) calculation using 7-day vs 28-day rolling averages for burnout/injury risk prediction — based on NFL sports science research
- Rule-based focus recommender analyzing striking vs grappling session ratios
- Statistical distribution analysis identifying neglected/underrepresented disciplines (<10% of total training time)

TESTING:
- Pytest test suite for ML engine covering edge cases: empty data, steady-state ACWR, acute load spikes, striker/grappler bias detection (7 test functions)

INFRASTRUCTURE:
- Docker Compose multi-container orchestration (Python app + MongoDB)
- Multi-stage Dockerfile (python:3.11-slim-bullseye, gcc build deps, no-cache pip install)
- Netlify frontend deployment configuration
- FastAPI static file serving for production SPA deployment with React Router catch-all

Focus on: system design, API architecture, full-stack integration, data modeling, and code quality. Make it sound impressive but honest.
```

---

# Machine Learning / Data Science Intern

```text
I need 4–5 resume bullet points for a project called "FightMetrics (MMA Tracker)" for a Machine Learning / Data Science Intern role. Use the STAR/XYZ format (action verb + what you did + tech + impact). Make them concise, quantifiable, and ATS-friendly.

Here are the verified technical facts from the codebase. Do NOT invent metrics — only use what's given:

PROJECT OVERVIEW:
- Built an ML-powered athletic analytics platform that uses unsupervised learning and sports science metrics to generate actionable training insights for combat sports athletes
- Solo-developed (personal project)

ML ENGINE DETAILS (engine.py — 129 lines, Scikit-Learn + Pandas + NumPy):

1. WEAKNESS IDENTIFICATION (Clustering + Statistical Analysis):
- K-Means clustering (k=3, scikit-learn) on 2D feature space (duration × intensity) to segment workout sessions into behavioral clusters
- Cluster center analysis: detects if ALL cluster centroids fall below duration threshold (60 min) or intensity threshold (7/10), indicating systematic training gaps
- Statistical distribution analysis: groupby aggregation on 8 discipline categories, flagging any discipline contributing <10% of total training volume as "underrepresented"
- Handles cold-start: gracefully degrades when <10 data points (skips clustering, falls back to distribution-only analysis)

2. BURNOUT RISK PREDICTION (ACWR — Rolling Average Regression):
- Computes training Load = Duration (min) × Intensity (1-10) per session
- Resamples time-series data to daily frequency using Pandas DatetimeIndex + resample('D')
- Calculates 7-day rolling mean (Acute Load) and 28-day rolling mean (Chronic Load)
- Derives Acute:Chronic Workload Ratio (ACWR) — a validated sports science metric used by NFL coaches
- Risk classification: Low (<1.2), Moderate (1.2–1.5), High (>1.5 — "Danger Zone")
- Epsilon smoothing (1e-6) to prevent division-by-zero in ratio calculation
- Fallback logic for insufficient history (<28 days → "Building baseline")

3. FOCUS RECOMMENDER (Rule-Based Classification):
- Binary classification of disciplines into striking (Boxing, Muay Thai) vs grappling (Wrestling, BJJ)
- Imbalance detection with 2:1 ratio threshold to recommend complementary training focus

DATA PIPELINE:
- Raw MongoDB documents → Pandas DataFrame transformation with datetime parsing
- Feature engineering: computed 'load' column (duration × intensity)
- Served via FastAPI async endpoint analyzing up to 1,000 most recent sessions per user

TESTING:
- 7 Pytest test functions covering: empty data handling, neglected discipline detection, steady-state ACWR verification, acute load spike detection (simulated 810 vs 90 load ratio), striker/grappler bias recommendations

TECH STACK: Python 3.12, Scikit-Learn ≥1.4, Pandas ≥2.2, NumPy ≥1.26, FastAPI, MongoDB (Motor async driver)

Focus on: ML algorithm selection and justification, feature engineering, data pipeline design, sports science domain knowledge, and testing methodology. Emphasize that this is applied ML solving a real-world problem.
```

---

# DevOps / Infrastructure / Platform Intern

```text
I need 4–5 resume bullet points for a project called "FightMetrics (MMA Tracker)" for a DevOps / Infrastructure Intern role. Use the STAR/XYZ format (action verb + what you did + tech + impact). Make them concise, quantifiable, and ATS-friendly.

Here are the verified technical facts from the codebase. Do NOT invent metrics — only use what's given:

PROJECT OVERVIEW:
- Full-stack web application with containerized deployment pipeline
- Solo-developed (personal project)

CONTAINERIZATION & ORCHESTRATION:
- Docker Compose multi-service architecture: Python FastAPI app + MongoDB with persistent volume mounts
- Multi-stage Dockerfile based on python:3.11-slim-bullseye — installs gcc + python3-dev build dependencies, then cleans apt cache (--no-install-recommends, rm -rf /var/lib/apt/lists/*) to minimize image size
- No-cache pip install (--no-cache-dir) for reproducible, lean image layers
- Environment variable injection for secrets (MONGODB_URI, SECRET_KEY, JWT config) — no hardcoded credentials

DEPLOYMENT & HOSTING:
- Netlify deployment configuration (netlify.toml) for frontend SPA
- FastAPI production SPA serving: mounts built React assets as static files, with catch-all route for React Router client-side navigation
- Nixpacks configuration (nixpacks.toml) for Railway/Render-style PaaS deployment
- Configurable CORS with environment-based origin whitelisting (comma-separated ALLOWED_ORIGINS)

APPLICATION ARCHITECTURE:
- Health check endpoint (/api/health) reporting: app status, backend framework, database connectivity (MongoDB ping), Python version, OpenSSL version — production-ready observability
- Async MongoDB connection lifecycle management (connect on startup, disconnect on shutdown) via FastAPI lifespan context manager
- TLS certificate pinning for MongoDB Atlas connections using certifi CA bundle
- 8 REST API endpoints across 3 modular route groups with dependency injection for auth

SECURITY:
- JWT stateless authentication (HS256 algorithm, configurable expiry via ACCESS_TOKEN_EXPIRE_MINUTES)
- bcrypt password hashing via passlib
- Bearer token scheme with automatic 401 handling on the frontend (Axios interceptors)

TESTING:
- Pytest test suite for core business logic (ML engine)
- conftest.py with shared fixtures for test isolation

TECH STACK: Docker, Docker Compose, Python/FastAPI, MongoDB, Netlify, Nixpacks, JWT, bcrypt

Focus on: containerization strategy, deployment pipeline, environment configuration, security practices, observability, and infrastructure-as-code. Emphasize production-readiness and operational maturity.
```

---

# Frontend / UI Engineering Intern

```text
I need 4–5 resume bullet points for a project called "FightMetrics (MMA Tracker)" for a Frontend / UI Engineering Intern role. Use the STAR/XYZ format (action verb + what you did + tech + impact). Make them concise, quantifiable, and ATS-friendly.

Here are the verified technical facts from the codebase. Do NOT invent metrics — only use what's given:

PROJECT OVERVIEW:
- Interactive athletic performance dashboard with real-time ML-powered training insights
- Solo-developed (personal project)

FRONTEND ARCHITECTURE (React 18 + TypeScript + Vite):
- Modular component hierarchy: App → AuthContext provider → Dashboard → 5 sub-components (StatsOverview, InsightsWidget, WorkoutForm, WorkoutHistory, WorkoutCharts)
- Separate Login and Register pages with form validation and error handling
- TypeScript throughout with strict type definitions (types/index.ts): User, Workout, WorkoutInput, AuthResponse, MLInsights, WorkoutStats interfaces
- Vite build system (rolldown-vite) with hot module replacement for fast iteration

STATE MANAGEMENT & DATA FLOW:
- React Context API (AuthContext) for global authentication state with useAuth custom hook
- Persistent sessions: JWT token stored in localStorage, auto-verified on mount via /auth/me endpoint
- Axios service layer (api.ts) with request interceptor for automatic Bearer token injection and response interceptor for 401 redirect handling
- Optimistic UI updates on workout creation (prepend to local state before re-fetch)

DATA VISUALIZATION & UX:
- Recharts integration: discipline breakdown bar charts and 7-day training timeline area charts
- GitHub-style weekly activity heatmap (M-T-W-T-F-S-S dots) with real-time completion tracking
- StatsOverview cards: total hours, total sessions, average intensity, discipline count
- AI Insights widget displaying ML-generated weakness analysis, burnout risk assessment, and focus recommendations

UI/UX POLISH:
- Dark/light theme toggle with CSS variable system and localStorage persistence
- Animated transitions (animate-fade-up with staggered delays)
- Toast notification system with auto-dismiss (3s timeout) and success/error variants
- TailwindCSS utility-first styling with custom design tokens (bg-card, text-ink, border-edge, etc.)
- Responsive layout (max-w-6xl centered) with tabbed navigation (Log / History / Analytics)
- Loading spinner with animated ring on initial data fetch
- Empty state designs with call-to-action buttons

CONSTANTS & CONFIGURATION:
- 8 combat discipline categories (Boxing, Wrestling, BJJ, Muay Thai, S&C, Cardio, Mobility, Sprints)
- Environment-based API URL configuration (VITE_API_URL)
- PWA-ready: manifest.json + service worker (sw.js) in public directory

Focus on: component architecture, state management patterns, data visualization, UX design decisions, TypeScript proficiency, and responsive design. Emphasize the polish and user experience.
```

---

# General / Catch-All SWE Intern

```text
I need 4–5 resume bullet points for a project called "FightMetrics (MMA Tracker)" for a general Software Engineering Intern role. Use the STAR/XYZ format (action verb + what you did + tech + impact). Make them concise, quantifiable, and ATS-friendly.

Here is a comprehensive summary of the project:

WHAT IT IS:
- A full-stack athletic performance tracking platform with ML-powered training insights, built for combat sports athletes (MMA, Boxing, BJJ, Muay Thai, Wrestling, etc.)
- Tracks workouts across 8 disciplines with duration, intensity, and notes
- Uses machine learning to identify training weaknesses, predict injury/burnout risk, and recommend focus areas

TECH STACK:
- Backend: Python 3.12, FastAPI (async), MongoDB (Motor async driver), Pydantic v2, JWT auth (bcrypt + python-jose)
- Frontend: React 18, TypeScript, Vite, TailwindCSS, Recharts, Axios
- ML: Scikit-Learn (K-Means clustering), Pandas, NumPy
- Infra: Docker Compose, Dockerfile, Netlify, Nixpacks

KEY TECHNICAL ACHIEVEMENTS:
1. Designed and built 8 RESTful API endpoints with async request handling, MongoDB aggregation pipelines, and JWT-secured routes with dependency injection
2. Engineered a custom ML engine (129 lines) implementing K-Means clustering for training pattern analysis and Acute:Chronic Workload Ratio (ACWR) for burnout prediction — a metric used by NFL teams
3. Built an interactive React dashboard with 5 modular sub-components, Recharts data visualizations, and a GitHub-style activity heatmap
4. Implemented full auth flow: registration, login, persistent sessions (JWT + localStorage), bcrypt hashing, Axios interceptors for token management
5. Containerized the full stack with Docker Compose (app + MongoDB + persistent volumes) and configured multi-platform deployment (Netlify + Nixpacks + FastAPI static serving)
6. Wrote 7 Pytest unit tests for the ML engine covering edge cases (empty data, load spikes, discipline bias)
7. Added dark/light theming, toast notifications, animated transitions, and responsive design for polished UX

Give me bullet points that span backend, frontend, ML, and infrastructure. Make each bullet start with a strong action verb. Keep each bullet to 1–2 lines max.
```


