# Bexar County Sheriff's Office — Website & Admin Panel

A public site for a roleplay sheriff's department. It has a roster, divisions, leadership, news, documents and a complaint form, plus a staff admin panel with an Internal Affairs dashboard and Discord webhook alerts.

## Tech
- React 19 + Vite + React Router (`src/`)
- Hono API running as a Netlify Server (`netlify/server/index.ts`, served on `/api/*`)
- Netlify Database (Postgres) via Drizzle ORM (`db/schema.ts`, migrations in `netlify/database/migrations`)
- Netlify Blobs for uploaded images and documents

## Run locally
Requires Node 24+.
```
npm install
netlify dev --port 8889
```
Admin panel: `/admin`. Owner account: `Gabyplays.dev.01`.

## Roadmap
- Replace the placeholder badge with the department's real seal
- Drag-and-drop ordering for roster and leadership
- Rich-text editing for news articles
