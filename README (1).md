# 🎓 RKV NEXUS AI

### Institution-Integrated AI-Powered Academic Assessment & Personalized Learning Platform

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Tests](https://img.shields.io/badge/tests-42%2F42%20passing-brightgreen)

---

## 📖 Table of Contents

1. [Project Overview](#1-project-overview)
2. [System Architecture](#2-system-architecture)
3. [Technology Stack](#3-technology-stack)
4. [Database Design](#4-database-design)
5. [API Architecture](#5-api-architecture)
6. [AI / Intelligence Layer](#6-ai--intelligence-layer)
7. [Security Architecture](#7-security-architecture)
8. [Complete Workflow](#8-complete-workflow)
9. [Feature List](#9-feature-list)
10. [Novelty](#10-novelty)
11. [Testing & Verification](#11-testing--verification)
12. [Deployment](#12-deployment)

---

## 1. Project Overview

**RKV NEXUS AI** is an institution-aware academic platform that unifies:

- Administration
- Examination
- Evaluation
- Personalized Learning

It connects **Admin**, **Faculty**, **Student**, and **Parent** on a single platform with complete data isolation between institutions.

The platform automates the full academic lifecycle — from institution onboarding and AI-generated exam creation to AI-powered evaluation (including handwritten answers) and personalized learning recommendations.

---

## 2. System Architecture

### High-Level Architecture

```text
┌─────────────────────────────────────────────────────────────────┐
│                              USERS                              │
│                Admin • Faculty • Student • Parent               │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                    REST API LAYER (FastAPI)                     │
│       JWT Authentication • Role Verification • Modular Routers  │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                      BUSINESS LOGIC LAYER                       │
│   Validation • CO Attainment • Exam Engine • Grading • Rules    │
└──────┬─────────────────────┬─────────────────────┬──────────────┘
       │                     │                     │
       ▼                     ▼                     ▼
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  PostgreSQL  │     │  AI Engine   │     │ Notification │
│  + pgvector  │     │    + LLM     │     │   Service    │
└──────────────┘     └──────────────┘     └──────────────┘
```

### Closed Feedback Loop

```text
Exam → Evaluation → CO Attainment → Knowledge State
  ↑                                        ↓
  ←──── AI Personalized Learning Plan ─────┘
```

### Layer Description

| Layer | Responsibility |
|-------|----------------|
| **Users** | Admin, Faculty, Student, Parent interact via web |
| **REST API** | FastAPI handles all requests with JWT auth |
| **Business Logic** | Validation, CO attainment, exam engine, rules |
| **PostgreSQL** | Stores all data with pgvector for AI similarity |
| **AI Engine** | Gemini 3.6 Flash + analytical engine + OCR |
| **Notification** | Email, in-app alerts, SSE push notifications |

---

## 3. Technology Stack

### Frontend

| Technology | Purpose |
|------------|---------|
| Next.js | React framework with SSR for performance and SEO |
| TypeScript | Type safety across all components |
| React | Component-based UI |
| Tailwind CSS | Utility-first styling |
| TanStack Query | Server state management, caching, auto-refresh |

### Backend

| Technology | Purpose |
|------------|---------|
| FastAPI | Modern, fast Python API framework |
| Python 3.12 | Backend language |
| JWT | Authentication with role verification |
| Pydantic | Data validation |
| SQLAlchemy | ORM for database operations |
| Alembic | Database migrations |

### Database

| Technology | Purpose |
|------------|---------|
| PostgreSQL | Relational database |
| pgvector | Embedding-based similarity search |

### AI / Intelligence Layer

| Technology | Purpose |
|------------|---------|
| Gemini 3.6 Flash | LLM for grading, recommendations, chatbot |
| Multimodal Vision | Handwritten OCR |
| Whisper API | Voice-to-text |
| OpenCV | Proctoring (face/object detection) |
| Analytical Engine | CO attainment, statistics, predictions |

### DevOps

| Technology | Purpose |
|------------|---------|
| Git / GitHub | Version control |
| Docker | Consistent development environment |
| Postman | API testing |
| Pytest | Backend test suite |

---

## 4. Database Design

### Two Main Hierarchies

#### Academic Hierarchy

```text
Institution
    ↓
Department
    ↓
Programme
    ↓
Academic Year
    ↓
Semester
    ↓
Subject
    ↓
Unit
    ↓
Topic
    ↓
Question
    ↓
Course Outcome (CO)
```

#### Student Hierarchy

```text
Student
    ↓
Subject Enrolment
    ↓
Examination
    ↓
Attempt
    ↓
Answers
    ↓
Evaluation
    ↓
Knowledge State
    ↓
Learning Plan
```

### Core Tables

| Table | Purpose |
|-------|---------|
| `users` | Admin, Faculty, Student, Parent accounts |
| `institutions` | Colleges/universities |
| `departments` | CSE, ECE, EEE, AIDS, etc. |
| `programmes` | B.E. CSE, B.Tech AI, etc. |
| `semesters` | 1–8 semesters per programme |
| `subjects` | AI, ML, Cloud, DBMS, etc. |
| `questions` | MCQ, Theory, Handwritten questions |
| `exams` | Exam configurations |
| `student_answers` | Student responses (text/images) |
| `evaluations` | Marks and feedback |
| `co_attainments` | CO-wise performance |
| `knowledge_states` | Student skill tracking |
| `learning_plans` | AI-generated recommendations |

### Advanced Tables

| Table | Purpose |
|-------|---------|
| `student_points` | Gamification points |
| `badges` | Achievement badges |
| `student_badges` | Earned badges |
| `performance_predictions` | AI performance forecast |
| `chat_sessions` | AI chatbot sessions |
| `chat_messages` | Chatbot messages |
| `adaptive_exams` | Adaptive difficulty tracking |
| `study_plans` | Personalized study plans |
| `study_plan_items` | Day-wise study items |
| `benchmarking_metrics` | Institution comparison |
| `knowledge_nodes` | Knowledge graph nodes |
| `knowledge_edges` | Knowledge graph edges |
| `dropout_predictions` | Dropout risk scores |
| `parents` | Parent accounts |
| `parent_student_mapping` | Parent-child mapping |
| `voice_submissions` | Voice answer recordings |
| `plagiarism_checks` | Plagiarism detection results |
| `academic_calendar` | Events and schedules |
| `user_2fa` | Two-factor authentication |
| `industry_skills` | Industry skill taxonomy |
| `co_skill_mapping` | CO to skill mapping |
| `certificates` | Blockchain certificates |

### Key Relationships

```text
users (1) ─── (N) student_enrolments
users (1) ─── (N) faculty_subjects
institutions (1) ─── (N) departments
departments (1) ─── (N) programmes
programmes (1) ─── (N) semesters
semesters (1) ─── (N) subjects
subjects (1) ─── (N) questions
exams (1) ─── (N) exam_questions
exams (1) ─── (N) student_answers
student_answers (1) ─── (1) evaluations
evaluations (1) ─── (N) co_attainments
```

---

## 5. API Architecture

### Modular Routers

| Router | Endpoints |
|--------|-----------|
| `/auth` | Login, register, forgot password, reset password |
| `/admin` | Dashboard stats, user management, institutions, audit logs |
| `/academics` | Institutions, departments, programmes, semesters, subjects |
| `/faculty` | Dashboard, exams, questions, evaluations, broadcasts |
| `/student` | Dashboard, exams, results, study plan, skills |
| `/evaluation` | Answer evaluation, CO attainment, faculty review |
| `/multimodal` | Handwritten upload, OCR, file serving |
| `/personalized-learning` | AI recommendations, knowledge state |
| `/notifications` | Broadcasts, alerts, SSE |
| `/chat` | AI chatbot sessions and messages |
| `/adaptive` | Adaptive exam start, answer, progress, submit |
| `/voice` | Voice upload, transcribe, submission |
| `/plagiarism` | Plagiarism check, report, flagged queue |
| `/calendar` | Events, auto-schedule, conflicts |
| `/skills` | Industry skills, student profile, placement readiness |
| `/gamification` | Points, badges, leaderboard |
| `/prediction` | Student performance, dropout risk |
| `/parent` | Parent login, child performance, notifications |

### Example API Flow — Student Exam Submission

```text
Student clicks "Start Exam"
  → POST /api/v1/student/exams/{id}/start

Student answers questions
  → POST /api/v1/student/exams/{id}/answer          (per question)

Student uploads handwritten answer
  → POST /api/v1/multimodal/upload-handwritten/{exam_id}/{question_id}

Student submits exam
  → POST /api/v1/student/exams/{id}/submit

Backend triggers evaluation
  → AI evaluates MCQ, theory, handwritten

CO attainment calculated
  → CO attainment engine runs

Knowledge state updated
  → Knowledge state service runs

AI generates recommendations
  → Personalized learning service runs

Student sees results
  → GET /api/v1/student/results/{id}
```

---

## 6. AI / Intelligence Layer

### Components

```text
┌─────────────────────────────────────────────────────────────┐
│                  AI / INTELLIGENCE LAYER                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─────────────────────┐     ┌─────────────────────┐        │
│  │  ANALYTICAL ENGINE  │     │    EXTERNAL LLM     │        │
│  │  (Runs on server)   │     │ (Gemini 3.6 Flash)  │        │
│  │                     │     │                     │        │
│  │  • CO Attainment    │     │  • Rubric Grading   │        │
│  │  • Statistics       │     │  • Explanations     │        │
│  │  • Knowledge State  │     │  • Recommendations  │        │
│  │  • Predictions      │     │  • Chatbot          │        │
│  └─────────────────────┘     └─────────────────────┘        │
│                                                             │
│  ┌─────────────────────┐     ┌─────────────────────┐        │
│  │      PGVECTOR       │     │   MULTIMODAL OCR    │        │
│  │  (Similarity Search)│     │   (Handwriting)     │        │
│  │                     │     │                     │        │
│  │  • Plagiarism       │     │  • Text Extraction  │        │
│  │  • Answer Matching  │     │  • Bounding Box     │        │
│  └─────────────────────┘     └─────────────────────┘        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### AI Capabilities

| Capability | Description |
|------------|-------------|
| Question Generation | AI generates MCQ, theory, handwritten questions by topic |
| Rubric Grading | LLM evaluates answers against rubrics with explanation |
| Counterfactual Feedback | "If you had written X, you would have earned +2 marks" |
| Handwritten OCR | Multimodal vision extracts text from handwriting |
| Personalized Recommendations | AI generates study plans based on weak areas |
| Chatbot | 24/7 academic mentor with student context |
| Adaptive Difficulty | Real-time ability calibration |
| Plagiarism Detection | pgvector embedding similarity search |
| Performance Prediction | Weighted algorithm predicting next semester |
| Dropout Prediction | ML model predicting dropout risk |
| Skill Mapping | Maps COs to industry skills |

---

## 7. Security Architecture

### Authentication Flow

```text
User Login
    ↓
Verify Email + Password (bcrypt)
    ↓
Generate JWT Token (contains user_id, role, institution_id)
    ↓
Send Token to User
    ↓
User includes Token in every request
    ↓
Server verifies Token signature
    ↓
Server checks role permissions
    ↓
Server checks institution isolation
    ↓
Data returned
```

### Security Layers

| Layer | Protection |
|-------|------------|
| **Authentication** | JWT with 24-hour expiry |
| **Authorization** | Role-based access control at API layer |
| **Data Isolation** | Institution-aware filtering |
| **Password** | Bcrypt hashing |
| **2FA** | TOTP + Email OTP |
| **SQL Injection** | SQLAlchemy ORM |
| **XSS** | Input sanitization |
| **CSRF** | Token-based protection |
| **Transport** | HTTPS in production |
| **Audit** | All actions logged with AI anomaly detection |

---

## 8. Complete Workflow

### Stage 1: Admin Setup
- Admin logs in
- Creates Institution → Department → Programme → Semester → Subject
- Assigns faculty to subjects
- Approves faculty registrations

### Stage 2: Faculty Registration & Login
- Faculty registers with Institution + Department + Employee ID
- Admin approves account
- Faculty logs in → sees assigned subjects

### Stage 3: Faculty Creates Exam
- Selects subject
- Enters exam details (title, duration, marks)
- Adds questions manually **or** AI generates questions
- Tags questions with CO
- Assigns to students (institution + department)
- Publishes exam

### Stage 4: Student Attempts Exam
- Student logs in
- Sees assigned exams
- Starts exam → timer begins
- Answers MCQ / Theory / Handwritten
- Uploads handwritten images (OCR processed)
- Submits exam

### Stage 5: AI Evaluation
- MCQ → auto-graded
- Theory → LLM evaluates with rubric
- Handwritten → OCR + LLM evaluates
- AI suggests marks + explanation + counterfactual feedback

### Stage 6: Faculty Review
- Views pending evaluations
- Sees AI suggested marks + rationale
- Accepts or modifies marks
- Adds feedback
- Confirms evaluation

### Stage 7: CO Attainment
- System maps marks to COs
- Calculates CO-wise performance
- Calculates class-wise CO attainment
- Flags weak COs (< 60%)

### Stage 8: Knowledge State Update
- Updates each student's knowledge map
- Identifies strong/weak topics
- Updates mastery levels

### Stage 9: AI Personalized Learning
- AI generates study plan
- Recommends resources
- Suggests practice questions
- Creates remedial path

### Stage 10: Feedback Loop
- Next exam informed by previous performance
- Continuous improvement cycle

---

## 9. Feature List

### Core Features
1. Multi-college institution management
2. Department and programme management
3. Faculty registration and approval
4. Student registration with validation
5. AI-powered exam creation
6. Question bank with CO mapping
7. MCQ, theory, and handwritten exams
8. AI evaluation with counterfactual feedback
9. Faculty review and override
10. CO attainment calculation
11. Knowledge state tracking
12. Personalized learning plans
13. Notifications and broadcasts
14. Audit logs and security monitoring

### Advanced Features (Part 1)
15. Gamification (points, badges, leaderboards)
16. Student performance prediction
17. AI chatbot with student context
18. Adaptive difficulty exams
19. Multi-language support (English, Tamil, Hindi)

### Advanced Features (Part 2)
20. AI-generated study plans
21. Institutional benchmarking
22. Knowledge graph for curriculum
23. Predictive dropout analysis
24. Parent portal
25. Voice-based answer submission
26. Advanced plagiarism detection
27. Smart academic calendar
28. Two-factor authentication
29. Industry skill mapping

### Advanced Features (Part 3 — Exam & Evaluation)
30. AI-powered proctoring
31. Emotion-aware exam interface
32. Collaborative group exams
33. Gamified exam levels
34. Offline exam mode
35. Voice-enabled exams
36. Flexible time exams
37. Peer assessment
38. Confidence score
39. Multi-evaluator consensus
40. Learning style evaluation
41. Improvement-based grading
42. Industry-validated evaluation

---

## 10. Novelty

RKV NEXUS AI combines the following in one integrated system:

1. Institution-aware multi-college architecture with complete data isolation
2. AI-powered handwritten evaluation with counterfactual guidance
3. Automated CO attainment tracking from every exam
4. Closed feedback loop — Exam → Evaluation → CO → Knowledge State → AI → Learning Plan
5. Adaptive difficulty exams with real-time ability calibration
6. Predictive dropout analysis with intervention recommendations
7. Voice-based answer submission in English, Tamil, and Hindi
8. Multi-language support including regional languages
9. Industry skill mapping with placement readiness scores
10. Blockchain certificate verification for tamper-proof credentials
11. 24/7 AI chatbot with student context
12. Parent portal for active participation
13. Gamification tied to real academic outcomes
14. Smart academic calendar with conflict-free scheduling
15. Knowledge graph for visual curriculum mapping

> No existing academic platform offers all of these in one integrated system.

---

## 11. Testing & Verification

### Test Results

| Test Suite | Result |
|------------|--------|
| Backend Test Suite | ✅ 42/42 PASSED (100%) |
| Full Platform Verification | ✅ 15/15 Milestones PASSED |
| Advanced Features (Part 1) | ✅ 5/5 PASSED |
| Advanced Features (Part 2) | ✅ 10/10 PASSED |
| Frontend Build (Next.js) | ✅ 0 Errors, 71 Routes |
| Client Build (Vite) | ✅ 0 Errors |

### Feature Verification

| Category | Status |
|----------|--------|
| Admin Dashboard | ✅ Verified |
| Student Registration | ✅ Verified |
| Faculty Dashboard | ✅ Verified |
| Exam Creation (AI) | ✅ Verified |
| Question Bank | ✅ Verified |
| Student Exam Attempt | ✅ Verified |
| AI Evaluation Pipeline | ✅ Verified |
| Faculty Review Queue | ✅ Verified |
| CO Attainment | ✅ Verified |
| Personalized Learning | ✅ Verified |
| Gamification | ✅ Verified |
| Performance Prediction | ✅ Verified |
| AI Chatbot | ✅ Verified |
| Adaptive Exams | ✅ Verified |
| Multi-Language Support | ✅ Verified |
| Study Plan | ✅ Verified |
| Benchmarking | ✅ Verified |
| Knowledge Graph | ✅ Verified |
| Dropout Analysis | ✅ Verified |
| Parent Portal | ✅ Verified |
| Voice Submission | ✅ Verified |
| Plagiarism Detection | ✅ Verified |
| Smart Calendar | ✅ Verified |
| Two-Factor Auth | ✅ Verified |
| Industry Skill Mapping | ✅ Verified |

---

## 12. Deployment

> The original documentation listed this section in the table of contents but did not include its content. Replace the placeholders below with your actual setup.

### Prerequisites
- Docker & Docker Compose
- Python 3.12
- Node.js (LTS)
- PostgreSQL with the `pgvector` extension

### Quick Start

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

# Configure environment variables
cp .env.example .env   # add DB URL, JWT secret, Gemini API key, etc.

# Run with Docker
docker compose up --build
```

### Backend (without Docker)

```bash
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload
```

### Frontend (without Docker)

```bash
cd frontend
npm install
npm run dev
```

### Run Tests

```bash
cd backend
pytest
```

---

## 📄 License

Add your license here (e.g., MIT).

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Please open an issue or submit a pull request.
