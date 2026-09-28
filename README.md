# EduGenie — Backend

Node.js + Express API powering EduGenie: AI Tutor chat, a text summarizer, a quiz
generator, and a study planner — all backed by Google Gemini via `@google/genai`.

## Requirements

- Node.js 18+
- A Google Gemini API key: https://aistudio.google.com/apikey

## Setup

```bash
cd backend
npm install
cp .env.example .env
# then edit .env and set GEMINI_API_KEY
```

## Run

```bash
npm run dev     # nodemon, auto-reload
# or
npm start       # plain node
```

The server starts on `http://localhost:5000` by default (configurable via `PORT`).

## Environment variables

| Variable          | Description                                   |
|-------------------|------------------------------------------------|
| `PORT`            | Port the server listens on (default `5000`)   |
| `GEMINI_API_KEY`  | Your Google Gemini API key (server-side only) |
| `FRONTEND_URL`    | Origin allowed by CORS (default `http://localhost:5173`) |

The Gemini API key is only ever read from `process.env.GEMINI_API_KEY` on the
server and is never sent to or exposed in the frontend.

## API

| Method | Endpoint            | Description                     |
|--------|----------------------|----------------------------------|
| GET    | `/`                  | Health check                    |
| POST   | `/api/chat`          | Ask the AI Tutor a question     |
| POST   | `/api/summary`       | Summarize a block of text       |
| POST   | `/api/quiz`          | Generate a multiple-choice quiz |
| POST   | `/api/study-plan`    | Generate a personalized study plan |

See the request/response shapes in each controller under `src/controllers/`.

## Project structure

```
src/
├── server.js                     # Express app, middleware, error handling
├── services/
│   └── geminiService.js          # All Gemini calls, prompts, JSON parsing/validation
├── controllers/
│   ├── chatController.js
│   ├── summaryController.js
│   ├── quizController.js
│   └── studyPlanController.js
└── routes/
    ├── chatRoutes.js
    ├── summaryRoutes.js
    ├── quizRoutes.js
    └── studyPlanRoutes.js
```
