# Agent notes

- **Frontend**: `src/` (SPA). Public pages are in `src/pages/Public.tsx` and `Resources.tsx`. Admin pages are in `src/pages/admin/`. The generic CRUD UI is `ResourceManager.tsx`. All styles are in `src/styles.css`, with CSS variables for the gold/charcoal theme.
- **API**: a single Hono app in `netlify/server/index.ts` handles `/api/*`. Helpers are in `server/` (`auth.ts` covers sessions, scrypt hashing and roles; `discord.ts` sends the webhook embed; `validate.ts` handles field parsing). Content CRUD is generated from the `resources` map.
- **SPA routing** is done with explicit redirects in `netlify.toml`. There's no `/*` catch-all, so it doesn't shadow the server. When you add a page route, add its redirect too.
- **Roles**: `owner` (only Gabyplays.dev.01; seeded by `ensureOwner()` from a stored hash), `admin`, `content`, `ia`. Keep `can()` in sync between `server/auth.ts` and `src/api.ts`.
- **Discord webhook URL**: stored in the `settings` table, falling back to the `DISCORD_WEBHOOK_URL` env var. Never return the full URL to the client.
- **Schema changes**: edit `db/schema.ts`, then run `npx drizzle-kit generate --name <name>`. Never edit applied migrations.
- **Files**: stored in the Blobs store `uploads`, with metadata in the `uploads` table. Internal files require a session.
