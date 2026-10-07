# Daywell
Daily sugar check-ins, date-specific tasks, walking steps, notes, monthly history and JSON export. No sample health records are preloaded.

## Run the MERN app
Requires Node 22.13+, npm, and MongoDB (local MongoDB or an Atlas connection string).

1. From the project root, run `npm install`.
2. Build React: `npx vite build --config mern/vite.config.mjs`.
3. Run `cd server` and `npm install`.
4. Copy `.env.example` to `.env` and set `MONGODB_URI`.
5. Run `npm start` and open http://localhost:4000.

The React app uses GET /api/days and PUT /api/days/:date. Express and Node serve both API and compiled frontend; Mongoose persists records in MongoDB. The API validates inputs. Writes are queued to keep save ordering. For frontend development, start the server and use `npx vite --config mern/vite.config.mjs` from the root.

This is a single-person local app: the server binds to 127.0.0.1 and does not implement multi-user authentication. Add authentication and per-user database ownership before exposing this MERN server publicly. Never commit server/.env. The separate private Sites deployment uses the same React interface with browser-local storage, not MongoDB; data does not automatically sync across browsers. Use Export my data to keep a backup. Dates use your device's local timezone. Tasks start fresh per day and can be edited for that day. Sugar check-ins mean added sugar, not all naturally occurring sugars.

## Verification
The React/Sites builds and Node syntax are checked. A live MongoDB connection is required to test persistence; no MongoDB service or credentials were supplied during creation.
