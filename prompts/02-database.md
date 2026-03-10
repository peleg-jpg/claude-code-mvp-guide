# Phase 2: Database Setup

**Mode: Normal (not Plan Mode)**

**Time: ~5 minutes**

---

## Prompt

```
Using the Supabase MCP, create the database tables we planned:

- trips (id uuid, user_id uuid references auth.users, destination text, budget numeric, days integer, start_date date, end_date date, created_at timestamptz)
- itinerary_days (id uuid, trip_id uuid references trips, day_number integer, plan_json jsonb)
- saved_flights (id uuid, trip_id uuid references trips, flight_data jsonb)

Add RLS (Row Level Security) policies:
- Users can only read/write their own trips
- Public can read trips via share URL (add is_public boolean to trips table)
- Enable RLS on all tables

Create the migration and apply it.
```

---

## What to expect

Claude will use the Supabase MCP to create tables directly in your Supabase project. You should see SQL being executed. Verify in your Supabase dashboard that the tables appeared.
