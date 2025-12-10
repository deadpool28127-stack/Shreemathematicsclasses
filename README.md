# Shree Mathematics Classes — Full Project (Vercel + Render)

This project contains:
- `frontend/` — Vercel-ready static frontend
- `backend/` — Express.js backend (Render-ready) with MongoDB + Google Sheets admission saving
- `docker-compose.yml` — optional local Docker development
- `README.md` — this file

## Quick overview

- Frontend is static and can be deployed to Vercel.
- Backend is an Express app to be deployed to Render. It stores data in MongoDB (MONGODB_URI) and appends admissions to a Google Sheet (optional) using a service account.
- For online classes we support **Google Meet links**: admin can create meeting entries with a link (we don't create Meet links via API; create them using Google Calendar/Meet and paste).

## Environment variables (backend)
Create a `.env` (or set environment variables in Render) with:

```
PORT=3000
MONGODB_URI=your_mongodb_connection_string
GOOGLE_SHEETS_SPREADSHEET_ID=your_spreadsheet_id (optional)
GOOGLE_SERVICE_ACCOUNT_KEY_PATH=service-account.json (path inside backend folder or set its content in env as GOOGLE_SERVICE_ACCOUNT_JSON)
ADMIN_USER=admin@shree
ADMIN_PASS=Shree@123
```

### Google Sheets setup (optional)
1. Create a Google Cloud project and enable the Google Sheets API.
2. Create a **service account**, download its JSON key.
3. Share the target Google Sheet with the service account email (editor).
4. Place the JSON in `backend/service-account.json` (or set env variable `GOOGLE_SERVICE_ACCOUNT_JSON` with the JSON content).
5. Set `GOOGLE_SHEETS_SPREADSHEET_ID` to the spreadsheet ID.

## Deploying frontend (Vercel)
1. Push `frontend/` to GitHub.
2. Connect the repo on Vercel and deploy.
3. In `frontend/script.js` change `API_BASE` to your backend URL (Render).

## Deploying backend (Render)
1. Push `backend/` to GitHub.
2. Create a Web Service on Render, connect the repo and branch.
3. Set the environment variables listed above.
4. Deploy.

## Local dev with Docker (optional)
```
docker-compose up --build
```

The frontend will be static; open `frontend/index.html` for quick testing.

