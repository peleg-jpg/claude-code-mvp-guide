# Trip Planner MVP

## Tech Stack
- Next.js 15 App Router, TypeScript
- Tailwind CSS + shadcn/ui components
- Supabase (auth + PostgreSQL database)
- Groq API with Llama 3.3 70B for trip generation (FREE - OpenAI-compatible)
- Kiwi.com Tequila API for flight search (FREE tier)
- Leaflet + OpenStreetMap for maps (FREE, no API key)
- Deploy on Vercel (FREE tier)

## Project Rules
- Hebrew UI (RTL layout with dir="rtl" on html element)
- Use Server Components by default, Client Components only when needed (forms, maps, interactive elements)
- All API keys in .env.local - never commit secrets
- Use Supabase MCP for database operations when possible
- Use Context7 for up-to-date docs (add "use context7" to prompts about Next.js, Supabase, Tailwind)
- One big prompt is better than many small ones - batch related tasks together

## Architecture
- /app - Next.js pages and API routes
- /app/api - Server-side API routes (Groq, Kiwi, Supabase)
- /components - Reusable UI components (shadcn/ui based)
- /components/ui - shadcn/ui primitives
- /lib - Utility functions, API clients, Supabase client
- /types - TypeScript interfaces

## Key Features (in build order)
1. Trip input form: destination, budget (USD), number of days, travel dates
2. AI-generated daily itinerary (food, attractions, tips per day) via Groq
3. Real flight search via Kiwi Tequila API with flexible date pricing
4. Interactive map showing attractions (Leaflet + OpenStreetMap)
5. Supabase Auth (Google + Email/Password)
6. Save trips to Supabase database
7. Share trip via public URL /trip/[id]

## API Integration Notes
- Groq: OpenAI-compatible, use `openai` npm package with baseURL: `https://api.groq.com/openai/v1`
- Kiwi Tequila: REST API, search endpoint: `https://api.tequila.kiwi.com/v2/search`
- Supabase: Use `@supabase/supabase-js` client, auth helpers for Next.js
