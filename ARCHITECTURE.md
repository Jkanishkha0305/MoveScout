# Architecture — MoveScout

> 🥇 1st Place — Best Use of LinkUp | NYC AI Agents Hack

## Agent Pipeline

```
  User Query: "Best neighborhood for a family moving to NYC under $3500/mo"
       │
       ▼
  ┌─────────────────────────────────────────────────────┐
  │              CrewAI Orchestrator                    │
  │                                                     │
  │  Agent 1: Location Scout                           │
  │  └─ LinkUp API → Real-time neighborhood data       │
  │     • Safety scores, school ratings, transit       │
  │                                                     │
  │  Agent 2: Market Researcher                        │
  │  └─ Perplexity API → Current market trends        │
  │     • Rental prices, availability, trends         │
  │                                                     │
  │  Agent 3: Neighborhood Scorer                      │
  │  └─ Synthesizes data → Ranked recommendations     │
  │     • Composite score per neighborhood             │
  │                                                     │
  │  Agent 4: Report Generator                        │
  │  └─ OpenAI → Natural language summary + top 3     │
  └─────────────────────────────────────────────────────┘
       │
       ▼
  Gradio Chat UI (voice + text)
  Top 3 neighborhoods with detailed breakdown
```

## Required API Keys (.env)

```
LINKUP_API_KEY=       # LinkUp real-time location data
PERPLEXITY_API_KEY=   # Market research and trends
OPENAI_API_KEY=       # Final synthesis and voice
```
