# SIGNIFY AI — AI-Powered Accessibility for Deaf Students


SIGNIFY AI is a real-time classroom accessibility assistant that converts spoken lecture audio into live captions, multi-language translations, and AI-generated study notes — ensuring deaf and hard-of-hearing students never miss a word.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎤 **Live Captions** | Real-time word-by-word transcription via Web Speech API |
| 🌍 **50+ Languages** | Auto-translate captions into any of 50 languages using MyMemory API |
| 🤖 **AI Lecture Summary** | Groq llama3-70b generates structured summaries, key points & exam questions |
| 💬 **Ask AI Tutor** | Ask questions about the lecture — streamed word-by-word via SSE |
| 📊 **Smart Dashboard** | Recharts engagement graphs, session statistics, quick exports |
| 💾 **Offline Archive** | All lectures stored in IndexedDB — searchable, filterable, permanent |
| ♿ **WCAG 2.1 Compliant** | High-contrast mode, reduce motion, adjustable font sizes |
| 🎭 **Demo Mode** | Simulates a live lecture stream — no microphone needed |
| 🔌 **Groq Fallback** | If Groq API unavailable, realistic mock responses are auto-generated |

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/your-team/signify-ai
cd signify-ai

# 2. Configure the server environment
cp server/.env.example server/.env
# Edit server/.env and add your GROQ_API_KEY

# 3. Install all dependencies (monorepo)
npm install

# 4. Start development servers (frontend + backend concurrently)
npm run dev
```

Open **http://localhost:5173** in Chrome or Edge for the best experience.

> **No Groq key?** The app still works! It falls back to intelligent mock responses derived from your actual transcript content.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | React 18 + Vite 5 + TailwindCSS 3 |
| **Animation** | Framer Motion 11 |
| **State** | Zustand 4 |
| **Routing** | React Router v6 |
| **AI** | Groq API (llama3-70b-8192) |
| **Speech** | Web Speech API (browser-native) |
| **Translation** | MyMemory Free API (no key required) |
| **Storage** | IndexedDB via `idb` library |
| **Charts** | Recharts |
| **Backend** | Node.js + Express.js (ES modules) |
| **Icons** | Lucide React |
| **Notifications** | react-hot-toast |

---

## 📁 Project Structure

```
signify-ai/
├── client/                        # React 18 + Vite frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── ai/                # LectureSummarizer, AskAI
│   │   │   ├── classroom/         # LiveCaptionPanel
│   │   │   ├── layout/            # Navbar, Sidebar, Layout
│   │   │   └── ui/                # Button, Badge, Modal, AnimatedText, StatsCard
│   │   ├── hooks/
│   │   │   ├── useSpeechRecognition.js   # Web Speech API + Demo simulator
│   │   │   ├── useGroqAI.js              # Summarize + SSE chat stream
│   │   │   └── useTranslation.js         # MyMemory debounce translation
│   │   ├── lib/
│   │   │   ├── db.js              # IndexedDB via idb
│   │   │   └── translate.js       # MyMemory API + cache
│   │   ├── pages/                 # Landing, Classroom, Dashboard, History, Settings
│   │   └── store/                 # Zustand stores (Caption, Lecture, Settings)
│   ├── tailwind.config.js         # Custom design tokens
│   └── vite.config.js             # Dev proxy → Express :3001
├── server/                        # Express.js backend
│   ├── routes/
│   │   ├── groq.js                # /api/groq/summarize + /api/groq/ask (SSE)
│   │   └── health.js              # /api/health
│   ├── middleware/
│   │   ├── cors.js
│   │   └── rateLimit.js
│   └── index.js
└── package.json                   # npm workspaces root
```

---

## 🎯 How It Works

```
Student enters classroom
        │
        ▼
  🎤 Microphone Input (Web Speech API)
        │
        ▼
  📝 Word-by-word captions displayed
        │
        ├──→ 🌍 Auto-translate (MyMemory API)
        │         └──→ Subtitle appears below caption
        │
        ├──→ 🤖 Generate Summary (Groq AI)
        │         └──→ Summary + Key Points + Exam Questions
        │
        ├──→ 💬 Ask AI Tutor (Groq SSE stream)
        │         └──→ Real-time typed response
        │
        └──→ 💾 Save to IndexedDB
                  └──→ Searchable in History page
```

---

## ⚙️ Environment Variables

```bash
# server/.env
GROQ_API_KEY=gsk_xxxxxxxxxxxx   # Get free at console.groq.com
PORT=3001
NODE_ENV=development
```

---

## 🧪 Testing Without Microphone

1. Navigate to the **Classroom** page
2. Click **"Try Demo"** in the bottom bar
3. Watch a simulated React & accessibility lecture stream in real-time
4. Use **"Ask AI Tutor"** to ask questions about the demo content
5. Click **"Generate Summary"** to see the full AI analysis

---
