# AuraTrip — Project Wiki

> Publish this as the `Home` page on https://github.com/AuraTrip/ai-meta/wiki

## Overview

AuraTrip is a travel planner web app where users can search destinations, plan trips with an AI travel agent, generate detailed itineraries, save trips, and view everything on an interactive map.

This wiki is the umbrella documentation home. Per-repo technical docs live in each repo's own wiki.

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     User (Browser)                      │
│                  AuraTrip/ui  (Next.js)                 │
└────────────┬──────────────────────────┬─────────────────┘
             │  REST + WebSocket        │  REST
             ▼                          ▼
┌────────────────────┐      ┌─────────────────────────┐
│  AuraTrip/api      │      │  AuraTrip/chat          │
│  Node.js/TypeScript│◄─────│  Claude AI Agent        │
│  Express/Fastify   │      │  (claude-sonnet-4-6)    │
│  PostgreSQL        │      │  Intent extraction       │
└────────────────────┘      └─────────────────────────┘
             │
             ▼
┌────────────────────┐
│  AuraTrip/ops      │
│  Terraform (AWS)   │
│  Kubernetes (EKS)  │
│  GitHub Actions    │
└────────────────────┘
```

---

## Repositories

| Repo | Role | Wiki |
|------|------|------|
| [AuraTrip/api](https://github.com/AuraTrip/api) | Backend REST API — destinations, itineraries, trips, auth | [api wiki](https://github.com/AuraTrip/api/wiki) |
| [AuraTrip/chat](https://github.com/AuraTrip/chat) | Claude AI agent — conversation, intent extraction, itinerary generation | [chat wiki](https://github.com/AuraTrip/chat/wiki) |
| [AuraTrip/ui](https://github.com/AuraTrip/ui) | Next.js frontend — all five user-facing features | [ui wiki](https://github.com/AuraTrip/ui/wiki) |
| [AuraTrip/ops](https://github.com/AuraTrip/ops) | Infrastructure as Code — Terraform, Kubernetes, CI/CD | [ops wiki](https://github.com/AuraTrip/ops/wiki) |
| [AuraTrip/ai-meta](https://github.com/AuraTrip/ai-meta) | AI orchestration, memory, handoffs, agent rules | this wiki |

---

## Features

### Search Destinations
- Users type a destination name or keyword
- Returns destination cards: photo, name, country, highlights
- Filter by region, activity type, budget
- **Owned by:** ui (search page) + api (`GET /api/destinations/search`)

### Chat with AI Travel Agent
- Conversational Claude-powered assistant
- Asks clarifying questions about dates, budget, interests
- Extracts structured travel intent as chips visible to the user
- **Owned by:** ui (chat panel) + chat (AI service)

### Generate Itineraries
- Day-by-day plan with activities, accommodation suggestions, transport tips
- Triggered from chat or directly via "Plan Trip" CTA
- **Owned by:** ui (itinerary page) + api (`POST /api/itineraries`) + chat (`POST /api/chat/itinerary`)

### Save Trips
- Authenticated users save planned trips
- View, revisit, and delete saved trips from profile
- **Owned by:** ui (saved trips page) + api (`/api/trips`)

### View on Map
- Interactive map (Mapbox/Leaflet) on search and itinerary pages
- Destination and itinerary stop pins with popups
- **Owned by:** ui (map component) + api (`GET /api/destinations/:id/geo`, `GET /api/trips/:id/map`)

---

## Active Work

- Umbrella issue: AuraTrip/ai-meta#TBD
- Sync note: [`sync/issues/2026-06-16-travel-planner.md`](https://github.com/AuraTrip/ai-meta/blob/main/sync/issues/2026-06-16-travel-planner.md)

---

## Key Decisions

| Decision | Rationale |
|----------|-----------|
| Claude API (`claude-sonnet-4-6`) for chat | Best-in-class instruction following; tool_use for structured itinerary output |
| PostgreSQL for api | Relational model fits destinations + trips + users; full-text search for destination search |
| Next.js for ui | SSR for SEO; file-based routing; strong TypeScript/Tailwind ecosystem |
| Terraform + EKS for ops | Reproducible infra; Kubernetes enables per-service scaling for api and chat |
| Secrets Manager for all API keys | Never store keys in repos; rotate without redeployment |
