# GitHub Issue: AuraTrip/ui — Frontend Features

**Title:** `Travel planner: destination search, AI chat, itinerary view, saved trips, and map`

**Labels:** `feature`, `frontend`

---

## Context

Part of the AuraTrip travel planner project. Umbrella: AuraTrip/ai-meta#TBD.

The ui repo is the Next.js frontend (TypeScript, Tailwind CSS, React Context).

## Goal

### 1. Destination Search UI (`pages/search.tsx`)
- Hero search bar with autocomplete suggestions
- Destination cards: image, name, country, highlights, "View on Map" and "Plan Trip" CTAs
- Filter sidebar: region, activity type, budget range
- Connects to: `GET /api/destinations/search`

### 2. AI Chat Interface (`components/ChatBot/`)
- Slide-in panel on search and itinerary pages
- WebSocket connection to chat service `/ws/chat/:conversationId`
- Message bubbles (user/assistant), typing indicator
- Extracted intent chips displayed below chat (shows parsed destination, dates, budget)
- Uses `useChatbot` hook and `ChatContext`

### 3. Itinerary View (`pages/itinerary/[id].tsx`)
- Day-by-day accordion: each day expands to show activities with time, name, description, location
- Map pin per activity linked to map view
- "Save Trip" CTA button (calls `POST /api/trips`)
- Print-friendly layout
- Connects to: `GET /api/itineraries/:id`

### 4. Saved Trips Page (`pages/trips.tsx`)
- Grid of trip cards: destination photo, name, dates, itinerary summary, edit/delete
- Empty state with CTA to start planning
- Requires auth — redirect to `/login` if unauthenticated
- Connects to: `GET /api/trips`, `DELETE /api/trips/:id`

### 5. Interactive Map View
- Mapbox GL JS (or Leaflet) embedded on search results and itinerary pages
- Destination pins from `GET /api/destinations/:id/geo`
- Trip stop pins from `GET /api/trips/:id/map` (GeoJSON FeatureCollection)
- Clicking a pin shows destination popup with name and "View" link

## Pointers

- `repos/ui/` in AuraTrip/ai-meta
- API: AuraTrip/api endpoints (destinations, itineraries, trips, geo)
- Chat: AuraTrip/chat WebSocket

## Blocked on

- `GET /api/destinations/search` in AuraTrip/api#TBD (destination search)
- `POST /api/itineraries` in AuraTrip/api#TBD (itinerary view)
- Chat WebSocket in AuraTrip/chat#TBD (chat panel)

## Links

- Umbrella: AuraTrip/ai-meta#TBD
- Sync note: `sync/issues/2026-06-16-travel-planner.md`
- Wiki (to be updated after implementation): https://github.com/AuraTrip/ui/wiki
