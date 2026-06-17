# GitHub Issue: AuraTrip/chat — AI Travel Agent

**Title:** `Travel planner: Claude-powered chat agent, intent extraction, and itinerary generation`

**Labels:** `feature`, `ai`

---

## Context

Part of the AuraTrip travel planner project. Umbrella: AuraTrip/ai-meta#TBD.

The chat repo is the AI service (Node.js/TypeScript or Python, FastAPI/Express, Claude API).

## Goal

### 1. AI Travel Agent Chat
- Multi-turn conversation using `claude-sonnet-4-6`
- System prompt: travel planning persona — friendly, knowledgeable, asks clarifying questions
- Existing endpoints: `POST /api/chat/messages`, `GET /api/chat/conversations/:id`
- WebSocket: `/ws/chat/:conversationId`

### 2. Intent / Requirement Extraction
- After each user turn, extract structured travel intent:
  ```json
  {
    "destination": "Paris",
    "startDate": "2026-08-10",
    "endDate": "2026-08-17",
    "passengers": { "adults": 2, "children": 0 },
    "budget": { "min": 1000, "max": 3000, "currency": "USD" },
    "preferences": ["museums", "food", "walking tours"]
  }
  ```
- Return as `extractedIntent` alongside `assistantMessage` in chat response
- Endpoint: `POST /api/chat/extract-context`

### 3. Itinerary Generation
- `POST /api/chat/itinerary` body: `{ destination, startDate, endDate, preferences, budget }`
- Uses Claude tool_use for structured output — returns typed itinerary JSON
- Day-by-day plan: activities with time, name, description, location, estimated cost
- Accommodation suggestions per day
- Transport tips between activities

## Pointers

- `repos/chat/` in AuraTrip/ai-meta
- AI provider: Anthropic Claude API (`claude-sonnet-4-6`)
- Called by: AuraTrip/api `POST /api/itineraries`

## Blocked on

- Claude API key provisioned in ops (AuraTrip/ops#TBD)

## Links

- Umbrella: AuraTrip/ai-meta#TBD
- Sync note: `sync/issues/2026-06-16-travel-planner.md`
- Wiki (to be updated after implementation): https://github.com/AuraTrip/chat/wiki
