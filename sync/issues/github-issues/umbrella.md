# GitHub Issue: AuraTrip/ai-meta — Umbrella

**Title:** `Umbrella: AuraTrip Travel Planner Web App`

**Labels:** `umbrella`, `epic`

---

## Context

AuraTrip is building a travel planner web app. This umbrella issue tracks all cross-repo work across four service repos: api, ui, chat, and ops.

## Goal

Ship a travel planner where users can:

- **Search destinations** — keyword/filter search with destination cards
- **Chat with an AI travel agent** — Claude-powered conversational assistant that extracts travel intent and recommends destinations
- **Generate itineraries** — AI-produced day-by-day travel plan with activities, accommodation, and tips
- **Save trips** — authenticated users can persist and revisit planned trips
- **View destinations on a map** — interactive map (Mapbox/Leaflet) plotting destinations and itinerary stops

## Pointers

| Repo | Responsibility | Sub-issue |
|------|---------------|-----------|
| [AuraTrip/api](https://github.com/AuraTrip/api) | Backend REST API, PostgreSQL, auth | TBD |
| [AuraTrip/chat](https://github.com/AuraTrip/chat) | Claude AI agent, intent extraction, itinerary gen | TBD |
| [AuraTrip/ui](https://github.com/AuraTrip/ui) | Next.js frontend, all five user-facing features | TBD |
| [AuraTrip/ops](https://github.com/AuraTrip/ops) | Terraform, Kubernetes, CI/CD pipelines | TBD |

Sub-issue links will be added as they are opened.

## Blocked on

Nothing currently. Sub-issues open in parallel.

## Links

- Sync note: `sync/issues/2026-06-16-travel-planner.md`
- Wiki: https://github.com/AuraTrip/ai-meta/wiki (to be created — see `sync/issues/wiki/ai-meta-home.md`)
