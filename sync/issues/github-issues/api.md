# GitHub Issue: AuraTrip/api — Backend Foundation

**Title:** `Travel planner: destination search, itinerary, saved trips, and map endpoints`

**Labels:** `feature`, `backend`

---

## Context

Part of the AuraTrip travel planner project. Umbrella: AuraTrip/ai-meta#TBD.

The api repo is the backend REST service (Node.js/TypeScript, Express/Fastify, PostgreSQL).

## Goal

Implement four new feature areas:

### 1. Destination Search
- `GET /api/destinations/search?q=&country=&type=&page=&limit=`
- Returns paginated destination list: `{ id, name, description, country, region, type, coordinates, imageUrl }`
- DB: `destinations` table with full-text search index

### 2. Itinerary Generation
- `POST /api/itineraries` body: `{ destinationId, startDate, endDate, preferences }`
- Delegates to chat service (`POST /api/chat/itinerary`) for AI-generated plan
- Returns: `{ id, destination, days: [{ date, activities: [{ time, name, description, location }] }] }`
- DB: `itineraries` table

### 3. Saved Trips CRUD
- `POST /api/trips` — save trip (requires auth JWT)
- `GET /api/trips` — list user's trips
- `GET /api/trips/:id` — get one trip
- `DELETE /api/trips/:id` — remove trip
- DB: `trips` table linked to `users`

### 4. Map / Geo Endpoints
- `GET /api/destinations/:id/geo` — returns GeoJSON Point for a destination
- `GET /api/trips/:id/map` — returns GeoJSON FeatureCollection of all stops in a trip

## Pointers

- `repos/api/` in AuraTrip/ai-meta
- Chat service: AuraTrip/chat (itinerary delegation)
- Auth: existing JWT middleware

## Blocked on

- Chat service itinerary endpoint (AuraTrip/chat#TBD) for `POST /api/itineraries`

## Links

- Umbrella: AuraTrip/ai-meta#TBD
- Sync note: `sync/issues/2026-06-16-travel-planner.md`
- Wiki (to be updated after implementation): https://github.com/AuraTrip/api/wiki
