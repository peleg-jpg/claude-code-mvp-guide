# Phase 4: AI Trip Generation

**Mode: Normal**

**Time: ~15 minutes**

---

## Prompt

```
use context7 for Next.js API routes.

Create the AI trip generation flow:

1. Install the openai npm package: npm install openai
2. Create /lib/groq.ts - Groq client using OpenAI SDK:
   - baseURL: "https://api.groq.com/openai/v1"
   - apiKey from env: GROQ_API_KEY
   - model: "llama-3.3-70b-versatile"

3. Create API route /app/api/generate-trip/route.ts that:
   - Accepts POST with: destination, budget (in ₪ ILS), days, startDate
   - Calls Groq with a structured prompt asking for a JSON response containing:
     - Daily itinerary (morning, afternoon, evening activities) - in Hebrew
     - Food recommendations per day (breakfast, lunch, dinner with ₪ price estimates)
     - Top attractions with descriptions and average entry cost in ₪
     - Detailed cost breakdown with REALISTIC prices for the destination:
       * Accommodation - TWO options:
         1. Central/tourist area: per-night rate in ₪
         2. Non-central/budget area: per-night rate in ₪
       * Food - TWO tiers:
         1. Mid-range restaurants: daily cost in ₪
         2. Luxurious dining: daily cost in ₪
       * Activities: average daily cost in ₪
       * Local transport: daily estimate in ₪
     - Total trip cost for each combination (central+mid, central+luxury, budget+mid, budget+luxury)
     - Local tips and cultural notes - in Hebrew
   - Streams the response back to the client

4. Create the results page /app/trip/[id]/page.tsx that displays:
   - Day-by-day cards with morning/afternoon/evening sections
   - Food recommendations with ₪ prices
   - Cost breakdown section showing:
     * Accommodation options side by side (central vs non-central)
     * Food tier comparison (mid-range vs luxurious)
     * Activities average
     * Total estimates for each combination
   - Map section placeholder (we'll add Leaflet next)

5. Connect the form submission on the homepage to this API route
6. Show a loading skeleton while generating
7. Store the generated trip in React state for now (we'll save to Supabase in Phase 6 after adding auth)

The Groq API uses the exact same format as OpenAI - just different baseURL.
All prices must be in ₪ (ILS). The Groq prompt should instruct the model to research realistic prices for the specific destination.
```

---

## What to expect

Claude will create the API route, Groq client, and results page. Test by submitting the form with a destination like "לונדון" (London) and budget of ₪5,000 for 5 days. You should see a streaming itinerary appear with realistic price breakdowns.

The cost breakdown should show 2 accommodation options and 2 food tiers so the user can mix and match.

If the Groq call fails, check your API key in `.env.local`.
