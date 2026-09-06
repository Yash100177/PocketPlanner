# PocketPlanner

PocketPlanner — a lightweight full‑stack planner with a React frontend and a Node/Express backend using MongoDB. The repo is split into frontend and backend so I can run and develop both parts independently.

---

## Repository (top-level)
- .gitattributes  
- .gitignore  
- Readme.md (this file)  
- frontend/  
- backend/  
- package-lock.json

---

## Overview
PocketPlanner is a simple planner app intended for local development and deployment as a static frontend backed by an API. The frontend was created with Create React App and is configured to proxy API requests to the backend during development. The backend is an Express app using Mongoose to connect to MongoDB and nodemon for automatic reload during development.

---

## Tech stack
- Frontend: React (Create React App / react-scripts), react-router-dom, styled-components, react-datepicker, chart.js, react-chartjs-2, react-csv, jspdf
- Backend: Node.js, Express, MongoDB (Mongoose), jsonwebtoken (JWT), bcrypt
- HTTP client: axios
- Dev tooling: react-scripts (frontend), nodemon (backend)

See frontend/package.json and backend/package.json for exact dependency versions.

---

## Environment (backend)
Create a `.env` file inside the backend folder with at least:
```
PORT=5000
MONGO_URI=<your-mongodb-connection-string>
JWT_SECRET=<your-jwt-secret>
```
Use your own values for the connection string and JWT secret. Do not commit secrets.

---

## Quick start (development)
I run backend and frontend in separate terminals.

1. Clone the repo:
```bash
git clone https://github.com/Yash100177/PocketPlanner.git
cd PocketPlanner
```

2. Start the backend:
```bash
cd backend
npm install
npm start
```
- `npm start` runs `nodemon app.js` (auto-reloads on changes).
- Default port is 5000 (set via `.env`).

3. Start the frontend:
```bash
cd frontend
npm install
npm start
```
- CRA dev server runs on http://localhost:3000.
- The frontend is configured with `"proxy": "http://localhost:5000"` in frontend/package.json so I can use relative API paths (e.g., `/api/...`) during development.

Open http://localhost:3000 in the browser.

---

## npm scripts (exact)

Frontend (frontend/package.json)
- start: `react-scripts start`
- build: `react-scripts build`
- test: `react-scripts test`
- eject: `react-scripts eject`

Backend (backend/package.json)
- start: `nodemon app.js`

Run examples:
```bash
# backend
cd backend
npm install
npm start

# frontend
cd frontend
npm install
npm start
```

---

## Build & deployment (concise)
Option A — Separate deployments
- Build frontend:
```bash
cd frontend
npm run build
```
Deploy the generated `build/` folder to a static host (Netlify, Vercel, GitHub Pages, etc.). Deploy the backend independently (Heroku, Render, Railway, etc.) and configure the frontend to call the deployed backend API.

Option B — Serve frontend from backend
- Build frontend (`npm run build`) and configure Express to serve the `build/` folder as static assets with a fallback to `index.html`. Deploy the backend; it will serve both API and frontend.

Note: during development the frontend uses `proxy: "http://localhost:5000"`; update API endpoints when using a deployed backend.

---

## Testing
- Frontend: `cd frontend && npm test` (CRA test runner).
- Backend: no test script is configured. I recommend adding Jest + supertest for API tests later.

---

## Notes & recommendations
- The frontend proxy forwards API requests to `http://localhost:5000` during development to avoid CORS changes.
- The backend uses nodemon so the server restarts on file changes.
- Keep secrets out of source control. Use environment variables or your host’s secret management.
- For quick MongoDB setup, I use a MongoDB Atlas URI in `MONGO_URI`.

---

## Contributing
If you want to contribute:
1. Fork the repo and create a branch (e.g., `feature/xyz`).
2. Make focused changes and include tests where applicable.
3. Open a pull request with a clear description.

For larger changes, open an issue first to discuss design and scope.

---

## Contact
Repository: https://github.com/Yash100177/PocketPlanner

Open an issue in the repo for questions, feedback, or collaboration.
