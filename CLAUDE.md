# Trip Planner MVP

## Tech Stack
- Next.js 15 App Router, TypeScript
- Tailwind CSS + shadcn/ui components
- Supabase (auth + PostgreSQL database)
- Groq API with Llama 3.3 70B for trip generation (FREE - OpenAI-compatible)
- SerpAPI Google Flights for flight search (FREE tier - 100 searches/month)
- Leaflet + OpenStreetMap for maps (FREE, no API key)
- Deploy on Vercel (FREE tier)

## Project Rules
- Hebrew UI with FULL RTL support:
  - dir="rtl" on html element
  - All text, labels, placeholders, and buttons in Hebrew
  - Form layouts flow right-to-left
  - Navigation items ordered RTL
  - Icons and arrows mirrored where needed (chevrons, back buttons)
  - Number inputs and sliders work naturally in RTL
- Currency: Israeli Shekels (ILS, symbol: ₪) everywhere - budget input, price displays, budget breakdowns
- Use Server Components by default, Client Components only when needed (forms, maps, interactive elements)
- All API keys in .env.local - never commit secrets
- Use Supabase MCP for database operations when possible
- Use Context7 for up-to-date docs (add "use context7" to prompts about Next.js, Supabase, Tailwind)
- One big prompt is better than many small ones - batch related tasks together

## Architecture
- /app - Next.js pages and API routes
- /app/api - Server-side API routes (Groq, SerpAPI flights, Supabase)
- /components - Reusable UI components (shadcn/ui based)
- /components/ui - shadcn/ui primitives
- /lib - Utility functions, API clients, Supabase client
- /types - TypeScript interfaces

## Key Features (in build order)
1. Trip input form: destination, budget (₪ ILS), synced days slider + date picker, flexible dates toggle
2. AI-generated daily itinerary (food, attractions, tips per day) via Groq - all prices in ₪
3. Real flight search via SerpAPI Google Flights with flexible date pricing
4. Trip cost breakdown with REAL estimated rates:
   - Flights: actual prices from SerpAPI
   - Accommodation: 2 options - central location vs non-central (cheaper)
   - Food: 2 tiers - mid-range vs luxurious, per day
   - Activities: average cost per day based on destination
   - Total trip cost estimate combining all categories
5. Interactive map showing attractions (Leaflet + OpenStreetMap)
6. Supabase Auth (Google + Email/Password)
7. Save trips to Supabase database
8. Share trip via public URL /trip/[id]

## Trip Cost Breakdown
The app must show a detailed cost breakdown based on real data, not guesses:
- **Flights**: Real prices from SerpAPI Google Flights search
- **Accommodation (2 options)**:
  - Central/tourist area hotel - higher price, better location
  - Non-central/budget area hotel - lower price, further from attractions
  - Groq generates realistic per-night rates based on destination
- **Food (2 tiers)**:
  - Mid-range: average restaurant meals per day
  - Luxurious: upscale dining per day
- **Activities**: Average daily cost for popular attractions/experiences
- **Total**: Sum of all categories, shown prominently
- All prices in ₪ (ILS)

## Synced Date Picker + Days Slider
The date range picker and days slider MUST stay in sync:
- If user picks start date May 1 and end date May 7 -> slider auto-updates to 7 days
- If user changes slider to 5 days -> end date auto-updates to May 5
- If user changes start date -> end date adjusts to keep the same number of days
- Both controls are the source of truth - last interaction wins

## Flexible Dates Feature
- Toggle: "I'm flexible with dates" checkbox
- When enabled: user picks a whole month (e.g., "May 2026") instead of exact dates
- Flight search queries the entire month and returns a price calendar
- Shows cheapest dates to fly within that month
- User can then select specific dates from the results

## API Integration Notes
- Groq: OpenAI-compatible, use `openai` npm package with baseURL: `https://api.groq.com/openai/v1`
- SerpAPI: REST API, endpoint: `https://serpapi.com/search.json?engine=google_flights`
- Supabase: Use `@supabase/supabase-js` client, auth helpers for Next.js
