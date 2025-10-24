# 🤖 AI Chatbots | Django + Next.js



![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![Django](https://img.shields.io/badge/Django-5.2-green?logo=django)
![Next.js](https://img.shields.io/badge/Next.js-15-black?logo=next.js)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-17-blue?logo=postgresql)
![LangChain](https://img.shields.io/badge/LangChain-Latest-green)


>
build conversational AI chatbots from  using Django, Django REST Framework, and Next.js. This hands-on project introduces you to LangChain and LangGraph basics while building a real working chatbot.

##  What Is This Project?

 how to integrate AI into full-stack web applications. It's NOT a comprehensive enterprise solution - it's a clear, straightforward  building your first conversational chatbot.

**What the project:**
- Setting up Django + Django REST Framework for AI applications
- Building a modern frontend with Next.js
- Creating basic conversational chatbot functionality
- Introduction to LangChain fundamentals
- LangGraph basics for conversation flows
- Connecting Django backend with AI services
- Deploying a simple AI chatbot

---
## 🛠️ Tech Stack (Enterprise-Grade Architecture)

This project features a production-ready, scalable architecture:

### Backend Stack (Django 5.2)
- **Django 5.2** - Latest Python web framework with async support
- **Django REST Framework** - Professional API development
- **PostgreSQL 17 + pgvector** - Advanced relational database with vector search
- **Redis 7** - High-performance caching & message broker
- **Celery** - Distributed task queue for background jobs
- **Celery Beat** - Cron-like task scheduler

### Frontend Stack (Next.js 15.5.4)
- **Next.js 15.5.4** - React framework with Turbopack (faster builds!)
- **Tailwind CSS 3.0** - Modern utility-first CSS framework
- **Axios** - Promise-based HTTP client
- **Server-Side Rendering (SSR)** - SEO-optimized, fast page loads

### AI/ML Integration
- **OpenAI API** - GPT-4 and GPT-3.5 Turbo integration
- **LangChain** - Advanced LLM application framework
- **LangGraph** - Stateful, multi-step conversation flows
- **pgvector Extension** - Vector similarity search for RAG
- **Conversation Memory** - Context-aware chatbot responses

### Infrastructure & DevOps
- **Docker Compose** - Multi-container orchestration
- **Automated Migrations** - Database schema management
- **Health Checks** - Service monitoring and auto-restart
- **Hot Reload** - Development efficiency (both backend & frontend)
- **Volume Persistence** - Data survives container restarts
- **Separate Entrypoints** - Optimized startup for each service

**What makes this project special:**
-  **Enterprise-grade architecture** - Production-ready patterns and best practices
-  **Fully automated setup** - Migrations, superuser, static files - all automatic
-  **Clear, documented code** - Professional code with comprehensive comments
-  **Step-by-step tutorials** - YouTube videos explaining architecture decisions
-  **Real production patterns** - Celery, Redis, proper database management
-  **Beginner-friendly** - Learn professional development without overwhelm

---

##  Key Features & Automation

### Automatic Setup (Zero Manual Steps!)

When you run `docker-compose up`, the system automatically:

1. **Database Initialization**
   - Waits for PostgreSQL to be fully ready
   - Runs all pending migrations
   - Creates database tables and indexes
   - Installs pgvector extension

2. **Superuser Creation**
   - Creates Django admin user automatically
   - **Username:** `admin`
   - **Password:** `admin123` (⚠️ Change in production!)
   - **Email:** `admin@aparsoft.com`
   - Ready to access admin panel immediately

3. **Static Files**
   - Collects all Django static files
   - Prepares admin interface assets
   - Configures file permissions

4. **Service Orchestration**
   - Backend starts first (runs migrations)
   - Celery workers wait for backend
   - Celery Beat waits for Redis
   - Frontend starts independently
   - All services connect automatically

### Django Admin Panel

Access the full-featured admin dashboard at: **http://localhost:8000/chatbot-admin/**

**Default Credentials:**
- Username: `admin`
- Password: `admin123`

**Admin Panel Features:**
- 👥 **User Management** - Create, edit, delete users and permissions
- 🗄️ **Database Models** - CRUD operations on all models
- 📧 **Email Verification** - Manage email addresses and verification
- 🔐 **Token Management** - API tokens and authentication
- 📊 **Celery Monitoring** - View periodic tasks and results
- 🔍 **Query Inspection** - Debug database queries
- 📝 **Content Management** - Manage site content and configuration

**Security Best Practices:**
```bash
# Change admin password immediately
docker-compose exec backend python manage.py changepassword admin

# Or create your own superuser
docker-compose exec backend python manage.py createsuperuser

# For production, delete default admin
docker-compose exec backend python manage.py shell
>>> from django.contrib.auth import get_user_model
>>> User = get_user_model()
>>> User.objects.get(username='admin').delete()
```

### Background Task Processing

**Celery Workers** handle:
- Asynchronous AI model requests
- Email sending
- Data processing
- Report generation
- Periodic cleanup tasks

**Celery Beat** schedules:
- Daily database backups
- Cache clearing
- Token expiration cleanup
- Periodic health checks

View Celery tasks in Django admin or use:
```bash
docker-compose exec celery celery -A config inspect active
```

### 🤖 Basic Chatbot Features
- **Conversational Interface** - Simple, clean chat UI
- **Message History** - Conversations that remember context
- **AI Responses** - Powered by OpenAI GPT models
- **User Sessions** - Multiple users can chat independently

### 🔧 Technical Implementation
- **Django REST API** - Clean, well-structured backend
- **Next.js Frontend** - Modern React with server-side rendering
- **LangChain Integration** - Your first steps with the AI framework
- **LangGraph Basics** - Simple conversation flow patterns
- **Database Storage** - Saving conversations in PostgreSQL

### 📚  Outcomes
- Understand how to connect Django with AI APIs
- Learn LangChain fundamentals through practice
- See how conversation state management works
- Deploy a full-stack AI application
- Build confidence to explore more complex AI features

**Required:**
- Python 3.10+ (we recommend 3.12)
- Node.js 18+
- OpenAI API key (we'll show you how to get one)

**Nice to have:**
- Docker Desktop (makes setup easier, but optional)
- Git basics

### 📦 Quick Setup

**Option 1: Docker (Recommended for Beginners)**
```bash
# Clone the repo
git clone https://github.com/Samuvel-victor/django-chatbot.git
cd django-nextjs-chatbot

# Create .env file (we'll guide you)
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY

# Start everything with one command!
docker-compose up --build
```

**What happens automatically:**
-  Database migrations run automatically
-  Superuser created (username: `admin`, password: `admin123`)
-  Static files collected
-  All services start and connect

**Access your application:**

| Service | URL | Credentials | Purpose |
|---------|-----|-------------|---------|
| **Frontend** | http://localhost:3000 | - | Main user interface |
| **Backend API** | http://localhost:8000 | - | REST API endpoints |
| **Admin Panel** | http://localhost:8000/chatbot-admin/ | admin / admin123 | Django admin dashboard |
| **PostgreSQL** | localhost:5433 | chatbot_user / chatbot_pass | Database access |
| **Redis** | localhost:6380 | - | Cache & broker |

**⚠️ Security Notice:** Default passwords are for development only! See [SYSTEM_SETUP.md](./SYSTEM_SETUP.md) for production security configuration.

---

## 📊 System Architecture

```
┌─────────────────────────────────────────────────────────┐
│              Docker Compose Orchestration               │
└─────────────────────────────────────────────────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
┌───────────────┐   ┌───────────────┐   ┌──────────────┐
│   Next.js     │   │    Django     │   │   Django     │
│   Frontend    │──▶│   Backend     │──▶│    Admin     │
│   Port 3000   │   │   Port 8000   │   │   Panel      │
└───────────────┘   └───────────────┘   └──────────────┘
                            │
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
┌───────────────┐   ┌───────────────┐   ┌──────────────┐
│  PostgreSQL   │   │     Redis     │   │   Celery     │
│  Port 5433    │   │   Port 6380   │   │   Workers    │
│  (Database)   │   │   (Cache)     │   │ (Background) │
└───────────────┘   └───────────────┘   └──────────────┘
                                                │
                                        ┌──────────────┐
                                        │ Celery Beat  │
                                        │ (Scheduler)  │
                                        └──────────────┘
```

**Key Features:**
-  All services containerized and isolated
-  Automatic service dependencies
-  Health checks and auto-restart
-  Data persistence across restarts
-  Hot reload for development

That's it! Everything is set up and ready to use.


**Step 1: Clone the Repository**
```bash
git clone https://github.com/aparsoft/django-nextjs-chatbot.git
cd django-nextjs-chatbot
```

**Step 2: Backend Setup (Django)**
```bash
# Navigate to backend folder
cd backend

# Create a virtual environment
python -m venv venv

# Activate virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate

# Install dependencies from requirements.txt
pip install -r requirements.txt

# Create .env file for backend
cp .env.example .env
# Edit .env and add your OPENAI_API_KEY

# Run database migrations
python manage.py migrate

# Create a superuser (optional, for admin access)
python manage.py createsuperuser

# Start the Django development server
python manage.py runserver
# Backend will run on http://localhost:8000
```

**Step 3: Frontend Setup (Next.js with .jsx)**
```bash
# Open a new terminal window
# Navigate to frontend folder
cd frontend

# Install Node.js dependencies
npm install
# or if you prefer yarn:
# yarn install

# Create .env.local file for frontend
cp .env.example .env.local
# Edit .env.local and set:
# NEXT_PUBLIC_API_URL=http://localhost:8000

# Start the Next.js development server
npm run dev
# or with yarn:
# yarn dev
# Frontend will run on http://localhost:3000
```

**Step 4: Test Your Setup**
- Open `http://localhost:3000` in your browser
- You should see the chatbot interface
- Try sending a message - it should connect to your Django backend
- Backend API docs available at `http://localhost:8000/api/docs`

**Troubleshooting Common Issues:**
- **Port already in use?** Change ports in settings
- **Module not found?** Make sure virtual environment is activated
- **Database errors?** Run migrations again
- **API not connecting?** Check CORS settings in Django

### 🔑 Getting Your OpenAI API Key

1. Go to [platform.openai.com](https://platform.openai.com/)
2. Sign up / Log in
3. Go to API Keys section
4. Create a new key

---
### 📺 Complete the project

**Part 1: Setup & Basics** (Start here!)
- "Introduction: What We're Building" - Project overview and goals
- "Django + Next.js Setup from Scratch" - Getting your environment ready
- "Your First API Call to OpenAI" - Hello World for AI

**Part 2: Building the Chatbot**
- "Creating the Django REST API" - Backend fundamentals
- "Next.js Frontend Setup" - Building the chat interface
- "Connecting Frontend to Backend" - Making them talk

**Part 3: Adding Intelligence**
- "Introduction to LangChain" - What it is and why we use it
- "Basic Conversation Memory" - Making the chatbot remember
- "Introduction to LangGraph" - Simple conversation flows

**Part 4: Deployment**
- "Docker Basics for Beginners" - Containerizing your app
- "Deploying Your First Chatbot" - Going live!

---
