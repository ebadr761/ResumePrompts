# FightMetrics — Resume Prompt Library

Prompts for generating resume bullet points from my **FightMetrics** project.

**Project identity:**  
FightMetrics is a **full-stack MMA training analytics platform** I built to track workouts and generate AI-driven insights for combat sports athletes.

Athletes log training across **8 disciplines** (Boxing, BJJ, Wrestling, Muay Thai, etc.), and the system analyzes patterns, weaknesses, and injury risk using sports science metrics.

Core stack:

- Backend: Python, FastAPI (async), MongoDB (Motor), Pydantic, JWT auth
- Frontend: React 18, TypeScript, Vite, Tailwind, Recharts
- ML: Scikit-Learn, Pandas, NumPy
- Infra: Docker Compose, Dockerfile, Netlify deployment

Key technical highlights:

- 8 REST API endpoints with JWT-secured routes and MongoDB aggregation pipelines
- React dashboard with modular components and interactive data visualizations
- ML engine analyzing training patterns with **K-Means clustering**
- **Acute:Chronic Workload Ratio (ACWR)** injury/burnout prediction (used in professional sports like the NFL)
- Containerized full stack with Docker
- Pytest unit tests for ML engine edge cases

Generate **4–5 resume bullet points using the STAR/XYZ format**:

**Action verb → what I built → tech used → impact**

Rules:

- Keep each bullet **1–2 lines max**
- Do **not invent metrics**
- Emphasize **technical depth + athlete performance analytics**
- Make bullets **ATS-friendly and concise**

---

# Software Engineering Intern

```text
Generate 4–5 resume bullet points for my project "FightMetrics (MMA Tracker)" targeting a Software Engineering Intern role.

Focus on:
- system design
- REST API architecture
- async backend development
- full-stack integration
- data modeling and authentication

Context:
FightMetrics is a full-stack MMA training analytics platform built with FastAPI, MongoDB, React, and TypeScript.

It includes:
- 8 async REST API endpoints
- JWT authentication with bcrypt
- MongoDB aggregation pipelines for workout analytics
- React dashboard with modular components and Recharts visualizations
- ML insights powered by K-Means clustering and ACWR workload analysis.

Use concise STAR/XYZ style bullets (action + tech + impact). Avoid invented metrics.
```

---

# Machine Learning / Data Science Intern

```text
Generate 4–5 resume bullet points for my project "FightMetrics (MMA Tracker)" targeting a Machine Learning / Data Science Intern role.

Focus on:
- applied ML
- feature engineering
- sports analytics
- data pipelines
- model reasoning

Context:
FightMetrics analyzes MMA training data to generate athlete performance insights.

The ML engine includes:
- K-Means clustering on workout duration × intensity to detect training pattern ruts
- Acute:Chronic Workload Ratio (ACWR) using 7-day vs 28-day rolling averages to estimate injury/burnout risk (a metric used by professional sports teams)
- Statistical analysis identifying undertrained disciplines
- Rule-based recommendations balancing striking vs grappling training.

Data pipeline:
MongoDB → Pandas DataFrame → feature engineering (training load = duration × intensity).

Use concise STAR/XYZ bullet points. No invented metrics.
```

---

# DevOps / Infrastructure Intern

```text
Generate 4–5 resume bullet points for my project "FightMetrics (MMA Tracker)" targeting a DevOps / Infrastructure Intern role.

Focus on:
- containerization
- deployment architecture
- environment configuration
- security and observability

Context:
FightMetrics is a containerized full-stack application.

Infrastructure includes:
- Docker Compose orchestration (FastAPI app + MongoDB)
- multi-stage Dockerfile based on python:3.11-slim
- environment variable secret management
- Netlify frontend deployment
- FastAPI serving React SPA assets
- health-check endpoint for system and database status
- JWT authentication and bcrypt password hashing.

Use concise STAR/XYZ bullet points. Emphasize production readiness.
```

---

# Frontend / UI Engineering Intern

```text
Generate 4–5 resume bullet points for my project "FightMetrics (MMA Tracker)" targeting a Frontend / UI Engineering Intern role.

Focus on:
- component architecture
- state management
- data visualization
- UX polish

Context:
FightMetrics includes a React + TypeScript dashboard for visualizing MMA training data.

Frontend features:
- modular component architecture with reusable dashboard components
- global auth state using React Context
- Axios interceptors for JWT authentication
- Recharts visualizations (discipline breakdowns and training timelines)
- GitHub-style activity heatmap
- dark/light theme toggle and responsive Tailwind UI.

Use concise STAR/XYZ bullet points emphasizing user experience and technical design.
```

---

# General Software Engineering Intern

```text
Generate 4–5 resume bullet points for my project "FightMetrics (MMA Tracker)" targeting a general Software Engineering Intern role.

Context:
FightMetrics is a full-stack training analytics platform for MMA athletes.

It combines:

- FastAPI backend with async REST APIs
- MongoDB workout data storage and aggregation analytics
- React + TypeScript dashboard with interactive visualizations
- ML insights including K-Means clustering and ACWR workload modeling
- Dockerized infrastructure with multi-environment deployment.

Focus on impactful bullets spanning backend, frontend, ML, and infrastructure.

Use concise STAR/XYZ bullet points (1–2 lines each).
```
