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

