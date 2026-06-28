# 🤖 AI Appointment Booking Bot

> A conversational AI assistant that sells and books appointments 24/7 across WhatsApp, Telegram, and web — powered by GPT-4o and synced with Google Calendar.
>
> ![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python&logoColor=white)
> ![FastAPI](https://img.shields.io/badge/FastAPI-0.110-009688?style=flat&logo=fastapi&logoColor=white)
> ![OpenAI](https://img.shields.io/badge/GPT--4o-OpenAI-412991?style=flat&logo=openai&logoColor=white)
> ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat&logo=postgresql&logoColor=white)
> ![Status](https://img.shields.io/badge/status-active-brightgreen)
>
> ---
>
> ## What it does
>
> This bot handles the full appointment funnel autonomously — from first contact to confirmed booking — without any human intervention. It understands natural language, answers questions about services and availability, and books time slots directly into Google Calendar.
>
> Businesses connect it to their existing WhatsApp number or Telegram bot, and it handles everything 24/7.
>
> ---
>
> ## Key Features
>
> - **Multi-channel** — runs on WhatsApp (via Twilio), Telegram Bot API, and embeddable web widget
> - - **Natural language understanding** — powered by GPT-4o for fluid, human-like conversations
>   - - **Real-time availability** — reads and writes Google Calendar to check open slots
>     - - **Full booking flow** — asks for service, date preference, confirms, and sends reminders
>       - - **Persistent context** — remembers conversation state across sessions using PostgreSQL
>         - - **Fallback handling** — gracefully escalates to a human agent when needed
>          
>           - ---
>
> ## Tech Stack
>
> | Layer | Technology |
> |---|---|
> | Backend | Python 3.11 + FastAPI |
> | AI | OpenAI GPT-4o (chat completions + function calling) |
> | Channels | WhatsApp (Twilio), Telegram Bot API, REST |
> | Calendar | Google Calendar API |
> | Database | PostgreSQL |
> | Deployment | Railway / Docker |
>
> ---
>
> ## Architecture
>
> ```
> ai-appointment-bot/
> ├── app/
> │   ├── api/
> │   │   ├── whatsapp.py       # Twilio webhook handler
> │   │   ├── telegram.py       # Telegram Bot API handler
> │   │   └── web.py            # REST endpoint for web widget
> │   ├── core/
> │   │   ├── agent.py          # GPT-4o conversation engine
> │   │   ├── calendar.py       # Google Calendar integration
> │   │   └── booking.py        # Booking logic & confirmation
> │   ├── db/
> │   │   └── models.py         # SQLAlchemy models
> │   └── main.py               # FastAPI entrypoint
> ├── Dockerfile
> └── requirements.txt
> ```
>
> ---
>
> ## How it works
>
> ```
> User sends "I'd like to book a haircut for tomorrow afternoon"
>         ↓
> GPT-4o parses intent, service type, and time preference
>         ↓
> Bot queries Google Calendar for available slots
>         ↓
> Bot proposes options: "I have 3pm or 4:30pm available — which works?"
>         ↓
> User confirms → appointment created in Google Calendar
>         ↓
> Confirmation sent via WhatsApp/Telegram with date, time, and details
> ```
>
> ---
>
> ## Setup
>
> ```bash
> git clone https://github.com/maxomart/ai-appointment-bot.git
> cd ai-appointment-bot
>
> # Set environment variables
> cp .env.example .env
> # Fill in: OPENAI_API_KEY, TWILIO_*, TELEGRAM_TOKEN, GOOGLE_CREDENTIALS, DATABASE_URL
>
> # Install dependencies
> pip install -r requirements.txt
>
> # Run locally
> uvicorn app.main:app --reload
>
> # Or with Docker
> docker build -t ai-appointment-bot .
> docker run --env-file .env -p 8000:8000 ai-appointment-bot
> ```
>
> ---
>
> ## Results
>
> - Handles appointment booking **24/7** with zero human intervention
> - - Reduced missed bookings for clients by eliminating phone-tag friction
>   - - Average booking flow completed in **under 3 minutes** per conversation
>    
>     - ---
>
> ## Author
>
> Built by [Joaquín](https://github.com/maxomart) — Full Stack Developer specializing in AI integrations and production SaaS.
> 
