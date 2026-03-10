# Phase 1: Plan the Architecture

**Mode: Plan Mode (press Shift+Tab first!)**

**Model: Opus 4.6** - Type `/model opus` before starting. Opus is smarter for architecture decisions. Planning uses few tokens, so the higher cost barely matters.

**Time: ~10 minutes**

Plan Mode is nearly free - Claude only reads and thinks, it doesn't write code. This saves you serious credits.

---

## Prompt

Copy and paste this into Claude Code:

```
use context7 for Next.js and Supabase docs.

Plan the complete architecture for this trip planner app. I need:

1. Database schema (Supabase tables for users, trips, itineraries, saved flights)
2. API routes structure - which routes, what each does
3. Page structure:
   - / (home - trip input form)
   - /trip/[id] (trip results with itinerary + flights + map)
   - /my-trips (saved trips list, requires auth)
4. Component tree - what components, which are Server vs Client
5. Data flow: user submits form -> API generates trip -> display results -> save to DB

Don't write any code yet. Just plan the architecture clearly.
```

---

## What to expect

Claude will output a structured plan. Review it. If something looks off, ask Claude to adjust before moving to Phase 2. Changes are free in Plan Mode.

**When you're happy with the plan: press Shift+Tab to exit Plan Mode**, then type `/model sonnet` to switch to Sonnet 4.6 for building (cheaper per token). Then move to Phase 2.
