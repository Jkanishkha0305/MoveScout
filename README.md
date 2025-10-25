# MoveScout

<p align="center">
  <img src="https://img.shields.io/badge/CrewAI-Multi--Agent-blueviolet?style=flat-square" />
  <img src="https://img.shields.io/badge/LinkUp%20API-Real%20Data-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/GPT--4-Powered-412991?logo=openai&style=flat-square" />
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi&style=flat-square" />
  <img src="https://img.shields.io/badge/Python-3.11-3776AB?logo=python&style=flat-square" />
</p>

> **AI relocation assistant** — a CrewAI multi-agent system that researches neighborhoods, jobs, housing costs, and lifestyle fit using **LinkUp's real-time data API** to recommend your best city to move to.

## Architecture

```
User Preferences
      │
      ▼
 Researcher Agent  ─── LinkUp API (jobs, housing, lifestyle data)
      │
      ▼
 Analyst Agent  ─── Cost-of-living + career opportunity scoring
      │
      ▼
 Recommender Agent  ─── Ranked city recommendations with reasoning
```

## Quick Start

```bash
git clone https://github.com/Jkanishkha0305/MoveScout.git
cd MoveScout
pip install -r requirements.txt
cp .env.example .env
# Add OPENAI_API_KEY and LINKUP_API_KEY to .env

python main.py --from "New York" --priorities "tech jobs, low cost, good weather"
```

## Tech Stack

- **CrewAI** — multi-agent orchestration
- **LinkUp API** — real-time city data (jobs, housing, lifestyle)
- **GPT-4** — reasoning and recommendation
- **FastAPI** — REST API wrapper
