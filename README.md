# EduGenie — AI Learning Assistant (Frontend)

A React + Vite frontend for EduGenie, a Gemini-powered learning assistant for college
students: AI Tutor chat, a text summarizer, a quiz generator, and a study planner.

## Requirements

- Node.js 18+
- The EduGenie backend running at `http://localhost:5000` (this frontend calls
  `http://localhost:5000/api/...` — see `src/services/api.js`)

## Run it

```bash
cd frontend
npm install
npm run dev
```

Then open the URL Vite prints (typically `http://localhost:5173`).

## Build for production

```bash
npm run build
npm run preview
```

## Project structure

```
src/
├── main.jsx              # React root + router
├── App.jsx                # Layout + routes
├── index.css               # Design tokens & global styles
├── components/
│   ├── Navbar.jsx          # Mobile top bar + drawer nav
│   ├── Sidebar.jsx         # Desktop/tablet nav
│   ├── FeatureCard.jsx     # Dashboard feature tile
│   ├── ChatBox.jsx         # AI Tutor chat UI
│   ├── MessageBubble.jsx   # Single chat message
│   ├── QuizCard.jsx        # Single quiz question
│   └── Loading.jsx         # Spinner
├── pages/
│   ├── Dashboard.jsx
│   ├── AIChat.jsx
│   ├── Summarizer.jsx
│   ├── Quiz.jsx
│   ├── StudyPlan.jsx
│   └── Profile.jsx
└── services/
    └── api.js               # All backend fetch calls
```

No Gemini API key is stored in this frontend — all AI calls go through your backend.
