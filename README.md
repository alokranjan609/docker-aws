# docker-aws

A collaborative code editor demo built with React, Vite, Monaco Editor, Yjs, and Socket.IO. The project includes a frontend application and an Express backend that hosts the production assets and provides real-time syncing via `y-socket.io`.

## Project Structure

- `frontend/` - React + Vite application
  - Uses `@monaco-editor/react` for the editor UI
  - Uses `yjs`, `y-monaco`, and `y-socket.io` for real-time collaborative editing
  - Tailwind-style classes are used in the UI styling
- `backend/` - Node/Express server
  - Serves static files from `public/`
  - Uses `socket.io` and `y-socket.io` for awareness and document synchronization
  - Includes a simple `/health` endpoint
- `Dockerfile` - builds the frontend and backend into a single production image

## Key Features

- Real-time collaborative editor
- User join flow via a username query parameter
- Live awareness of connected users
- Production-ready build using Docker multi-stage build

## Local Development

### Backend

From the project root:

```bash
cd backend
npm install
npm run dev
```

Then open the app in your browser at `http://localhost:3000`.

### Frontend

From the project root:

```bash
cd frontend
npm install
npm run dev
```

Vite will start the frontend dev server and show the local URL in the terminal.

## Production Build

From the project root:

```bash
docker build -t docker-aws-app .
```

Then run the container:

```bash
docker run --rm -p 3000:3000 docker-aws-app
```

The application will be available at `http://localhost:3000`.

## Notes

- The frontend builds into `dist/`, and the Dockerfile copies that folder into the backend `public/` directory.
- The backend server is configured to listen on port `3000`.
- The editor uses Monaco and Yjs to synchronize text updates across connected clients.

## Useful Commands

- `npm run dev` (backend) - start backend with nodemon
- `npm run dev` (frontend) - start Vite dev server
- `npm run build` (frontend) - create production frontend build
- `npm run preview` (frontend) - preview built frontend

## How to Use

1. Start the app in development or production.
2. Open the URL in your browser.
3. Enter a username and click `Join`.
4. Share the same URL with other users to collaborate in real time.

## Dependencies

- Backend: `express`, `socket.io`, `y-socket.io`
- Frontend: `react`, `react-dom`, `vite`, `@monaco-editor/react`, `yjs`, `y-monaco`, `y-socket.io`
