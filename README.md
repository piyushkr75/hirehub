# HireHub Job Portal

This is a MERN-style app with a Node/Express + MongoDB backend and a Vite/React frontend.

## Prerequisites
- Node.js (LTS recommended)
- MongoDB (local or Atlas)
- Cloudinary account (backend starts Cloudinary config on boot)

## Project Layout
- `backend/` - Express API (MongoDB via Mongoose)
- `frontend/` - React (Vite) UI

## Environment Variables
The backend uses these variables:
- `DATABASE_CONNECTION_URL`
- `JWT_SECRET`
- `CLOUDINARY_CLOUD_NAME`
- `CLOUDINARY_API_KEY`
- `CLOUDINARY_API_SECRET`
- `PORT` (optional)

The frontend uses:
- `VITE_BACKEND_URL`

### 1) Backend `.env`
1. Go to `backend/`
2. Copy `backend/.env.example` to `backend/.env`
3. Fill in the values

Notes:
- The backend will connect to MongoDB database name `hirehub-job-portal` automatically (it appends `/${dbName}` in code). So `DATABASE_CONNECTION_URL` should be your Mongo connection string **without** a trailing database name and (recommended) without a trailing `/`.
- If you're running Mongo locally, prefer `DATABASE_CONNECTION_URL=mongodb://127.0.0.1:27017` (your current error shows `::1:27017`, which is IPv6 localhost and often causes `ECONNREFUSED`).

### 2) Frontend `.env`
1. Go to `frontend/`
2. Copy `frontend/.env.example` to `frontend/.env`
3. Set `VITE_BACKEND_URL` to your backend URL (example: `http://localhost:5000`)

## How to Run
Run backend and frontend in separate terminals.

### Backend
1. Open a terminal in `backend/`
2. Install dependencies:
   - `npm install`
3. Start the server:
   - `npm run server`
4. The API will be available at `http://localhost:5000` (or your configured `PORT`).

### Frontend
1. Open a terminal in `frontend/`
2. Install dependencies:
   - `npm install`
3. Start the dev server:
   - `npm run dev`
4. Open the URL shown by Vite (typically `http://localhost:5173`).

## API Base Routes (for reference)
Backend routes are mounted like:
- `/user/*`
- `/company/*`
- `/job/*`

The frontend calls them using `VITE_BACKEND_URL` + the route paths above.

## Deploy Note (Vercel)
There is a `backend/vercel.json` that routes requests to `server.js`. If you deploy the backend separately, ensure the same environment variables are configured in your Vercel project.

