# MoveScout 🏠

**AI-Powered Moving Assistant** — Your top space for moving via AI agents. Built at the NYC AI Agents Hackathon (October 2025).

![Python](https://img.shields.io/badge/Python-3.11+-blue?style=flat&logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-blue?style=flat&logo=fastapi)
![Gradio](https://img.shields.io/badge/Gradio-4.x-purple?style=flat)
![LangChain](https://img.shields.io/badge/LangChain-0.3.x-green?style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat)

## 🏆 Winner — NYC AI Agents Hackathon

MoveScout won the **Creators Corner** track at the NYC AI Agents Hackathon (October 4-10, 2025). The platform uses multiple AI agents to help users find the best moving companies through intelligent negotiation.

## What It Does

MoveScout uses **AI agents** to:

- **Research moving companies** via Perplexity API for real-time market data
- **Negotiate better prices** with movers using AI-driven strategies
- **Provide voice interaction** via Twilio for hands-free queries
- **Track prices** and alert users when deals improve

## Tech Stack

- **Backend**: FastAPI + Python
- **AI Agents**: LangChain + LangGraph
- **Database**: Firebase Firestore
- **Frontend**: Gradio UI
- **Voice**: Twilio + WebSocket
- **Search**: Perplexity API + LinkUp integration

## Getting Started

### Prerequisites

- Python 3.11+
- Twilio account (for voice)
- Perplexity API key (for market research)
- Firebase project (optional, for production)

### Installation

```bash
# Clone the repo
git clone https://github.com/Jkanishkha0305/MoveScout.git
cd MoveScout

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys
```

### Running the App

```bash
# Backend API (FastAPI)
python app.py

# Frontend UI (Gradio) - in another terminal
python gradio_app.py

# Or run both together
bash deploy.sh
```

The Gradio interface will be available at `http://localhost:7860`

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    MoveScout Architecture                   │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐              │
│  │  Voice   │───▶│  FastAPI │◀───│ Gradio   │              │
│  │ (Twilio) │    │   Server │    │    UI    │              │
│  └──────────┘    └────┬─────┘    └──────────┘              │
│                       │                                     │
│                       ▼                                     │
│                ┌──────────────┐                             │
│                │ Agent Graph  │                             │
│                │  (LangChain) │                             │
│                └──────┬───────┘                             │
│                       │                                     │
│    ┌──────────────────┼──────────────────┐                │
│    ▼                  ▼                  ▼                 │
│ ┌────────┐     ┌────────────┐     ┌───────────┐           │
│ │Strategist│    │   Analyst  │     │    Voice  │           │
│ │ Agent   │     │   Agent    │     │   Agent   │           │
│ └────┬───┘     └─────┬──────┘     └─────┬─────┘           │
│      │               │                  │                  │
│      └───────────────┼──────────────────┘                  │
│                      ▼                                      │
│            ┌─────────────────┐                              │
│            │  Firebase / DB  │                              │
│            └─────────────────┘                              │
└─────────────────────────────────────────────────────────────┘
```

## Project Structure

```
MoveScout/
├── agents/                  # AI agent implementations
│   ├── strategist_agent.py  # Price negotiation agent
│   ├── analyst_agent.py     # Market analysis agent
│   ├── chat_agent.py        # General chat agent
│   ├── voice_agent.py       # Voice interaction agent
│   ├── agent_graph.py       # LangGraph agent orchestration
│   └── state_models.py      # Pydantic data models
├── integrations/            # External API integrations
│   └── perplexity_client.py # Perplexity search API
├── app.py                   # FastAPI backend
├── gradio_app.py            # Gradio frontend
├── voice_server.py          # Twilio voice server
├── requirements.txt         # Python dependencies
└── Dockerfile               # Docker deployment
```

## Environment Variables

```env
# OpenAI
OPENAI_API_KEY=sk-...

# Perplexity (for market research)
PERPLEXITY_API_KEY=pplx-...

# Firebase (optional, for production)
FIREBASE_ADMIN_CERT_PATH=firebase_adminsdk.json
DEMO_MODE=true  # Set to false for production

# Twilio (for voice)
TWILIO_ACCOUNT_SID=AC...
TWILIO_AUTH_TOKEN=...
TWILIO_PHONE_NUMBER=+1...

# LinkUp (for real-time search)
LINKUP_API_KEY=...
```

## Demo Mode

The app runs in **Demo Mode** by default, which uses simulated data instead of real Firebase. Set `DEMO_MODE=false` in your `.env` for production.

## Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

MIT License — see LICENSE for details.

## Acknowledgments

- **NYC AI Agents Hackathon** — For the amazing event and platform
- **LangChain** — For the excellent agent framework
- **Perplexity** — For real-time search capabilities
- **LinkUp** — For real-time moving company data
