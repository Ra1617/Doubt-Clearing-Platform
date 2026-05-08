# Doubt Clearing Platform

A web app for handling academic doubts without turning the process into email chaos.

Students can raise questions, attach supporting files, and track what happens next. Faculty can review incoming doubts, post answers, and close the loop. Admins can manage users and keep an eye on the system from one place.

## What is inside

- FastAPI backend for auth, doubt handling, faculty actions, and admin tools.
- React frontend built with Vite for the student-facing flow.
- AI-assisted matching for similar doubts and answer suggestions.
- Supabase storage support for uploaded images.
- Role-based access for students, teachers, and admins.

## Project layout

- `backend/` - FastAPI app, database setup, schemas, and service code.
- `clearmydoubt-frontend/` - Vite app used by the current UI.
- `frontend/` - extra frontend source tree used for shared UI pieces.

## Requirements

- Python 3.10 or newer
- Node.js 18 or newer
- PostgreSQL or a Supabase database
- A Supabase storage bucket for images

## Environment setup

Create a `backend/.env` file and fill in the values your app needs. Keep it local.

```env
DATABASE_URL=postgresql://user:password@host:5432/dbname
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
SUPABASE_STORAGE_BUCKET=doubt-images
JWT_ACCESS_SECRET=change-this
JWT_REFRESH_SECRET=change-this-too
FRONTEND_URL=http://localhost:3000
PORT=4000
```

If you use the frontend dev server, set `clearmydoubt-frontend/.env.local` when needed.

```env
VITE_API_BASE_URL=http://127.0.0.1:4000
```

## Run the backend

From the `backend/` folder:

```bash
pip install -r requirements.txt
uvicorn app.main:app --reload --port 4000
```

The API root should answer on `http://127.0.0.1:4000/`.

## Run the frontend

From `clearmydoubt-frontend/`:

```bash
npm install
npm run dev
```

By default, the frontend talks to `http://127.0.0.1:4000`.

## Main flows

- Student registration and login.
- Doubt submission with text and optional images.
- Faculty review, resolution, and image uploads.
- Admin user management, doubt tracking, and AI config updates.

## API overview

- `POST /auth/register` - create a student account.
- `POST /auth/login` - sign in and receive tokens.
- `POST /doubts/` - submit a new doubt.
- `GET /doubts/my` - list the current student’s doubts.
- `GET /faculty/doubts` - view doubts assigned to faculty.
- `POST /faculty/doubts/{id}/resolve` - post a resolution.
- `GET /admin/users` - list users.
- `GET /admin/doubts` - inspect all doubts.

## Safety notes

- Keep `.env` files out of git.
- Do not store secrets in the frontend.
- Rotate keys if anything sensitive was exposed before.

## Contributing

Make changes on a branch, keep commits tight, and open a pull request when the work is ready. Clear diffs make review easier.

## License

Add the license your project uses here if it is not already set.
