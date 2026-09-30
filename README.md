# 🎓 AI Study Buddy - Backend API

AI Study Buddy is an AI-powered study assistance backend built with **Node.js**, **Express**, **MongoDB**, and **Google Gemini AI**. It helps students learn faster and more effectively by automatically analyzing study materials to generate concise summaries, flashcards, interactive quizzes, and customized study schedules.

---

## ✨ Features

- 🔐 **Authentication & Authorization**: Secure user registration and login with JWT and bcrypt password hashing.
- 📄 **Material Upload**: Support for uploading study documents (`.txt`, `.md`, `.pdf`) via Multer.
- 🤖 **AI-Powered Summarization**: Generate concise, revision-ready summaries of study materials using Gemini AI.
- 🃏 **Smart Flashcards**: Automatically generate question-and-answer flashcard sets from uploaded content.
- 📝 **Quiz Generation**: Create 5-question multiple choice quizzes based on study documents.
- 📅 **Custom Study Plans**:
  - Generate study plans based on specific uploaded material.
  - Generate personalized study schedules based on learning goals, available hours, and exam dates.

---

## 🛠️ Tech Stack

- **Runtime**: [Node.js](https://nodejs.org/)
- **Framework**: [Express.js](https://expressjs.com/)
- **Database**: [MongoDB](https://www.mongodb.com/) with [Mongoose](https://mongoosejs.com/)
- **AI Integration**: [Google Generative AI (Gemini)](https://ai.google.dev/)
- **Authentication**: [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) & [bcryptjs](https://github.com/dcodeIO/bcrypt.js)
- **File Uploads**: [Multer](https://github.com/expressjs/multer)

---

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher recommended)
- MongoDB instance (local or MongoDB Atlas)
- Google Gemini API Key

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Tanya926/AI-Study-Buddy.git
   cd AI-Study-Buddy
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure Environment Variables:**
   Create a `.env` file in the root directory (refer to `.env.example`):
   ```env
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   JWT_ACCESS_SECRET=your_jwt_secret_key
   GEMINI_API_KEY=your_gemini_api_key
   CLIENT_URL=http://localhost:3000
   ```

4. **Start the server:**
   ```bash
   # Production mode
   npm start

   # Development mode (with nodemon)
   npx nodemon index.js
   ```

   The server will start at `http://localhost:5000`.

---

## 📡 API Endpoints

### 🔐 Auth Routes (`/api/auth`)

| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `POST` | `/api/auth/register` | Register a new user | No |
| `POST` | `/api/auth/login` | Log in and receive JWT token | No |

### 📚 Study Materials (`/api/materials`)

All material endpoints require a `Bearer <token>` in the `Authorization` header.

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/materials/upload` | Upload study file (`multipart/form-data`) |
| `POST` | `/api/materials/:id/summarize` | Generate AI summary for a material |
| `POST` | `/api/materials/:id/flashcards` | Generate AI flashcards |
| `POST` | `/api/materials/:id/quiz` | Generate AI multiple-choice quiz |
| `POST` | `/api/materials/:id/study-plan` | Generate a study plan from the material |

### 🧠 AI Planner (`/api/ai`)

| Method | Endpoint | Description | Auth Required |
|---|---|---|---|
| `POST` | `/api/ai/study-plan` | Generate personalized study schedule | Yes |

---

## 📂 Project Structure

```text
AI-Study-Buddy/
├── src/
│   ├── controllers/
│   │   ├── adminController.js
│   │   ├── authController.js
│   │   └── materialController.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── upload.js
│   ├── models/
│   │   ├── Material.js
│   │   └── User.js
│   ├── routes/
│   │   ├── admin.js
│   │   ├── aiRoutes.js
│   │   ├── auth.js
│   │   └── materials.js
│   └── utils/
│       ├── db.js
│       ├── gemini.js
│       └── tokens.js
├── uploads/              # Uploaded user files
├── .env.example          # Environment variables template
├── .gitignore
├── index.js              # Server entry point
├── package.json
└── README.md
```

---

## 📄 License

This project is licensed under the ISC License.
