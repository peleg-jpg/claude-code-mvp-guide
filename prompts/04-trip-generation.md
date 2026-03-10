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
   - Accepts POST with: destination, budget, days, startDate
   - Calls Groq with a structured prompt asking for a JSON response:
     - Daily itinerary (morning, afternoon, evening activities)
     - Food recommendations per day (breakfast, lunch, dinner with price estimates)
     - Top attractions with descriptions
     - Budget breakdown (accommodation, food, transport, activities)
     - Local tips and cultural notes
   - Streams the response back to the client

4. Create the results page /app/trip/[id]/page.tsx that displays:
   - Day-by-day cards with morning/afternoon/evening sections
   - Food recommendations with estimated prices
   - Budget tracker showing spent vs remaining
   - Map section placeholder (we'll add Leaflet next)

5. Connect the form submission on the homepage to this API route
6. Show a loading skeleton while generating
7. Store the generated trip in React state for now (we'll save to Supabase in Phase 6 after adding auth)

The Groq API uses the exact same format as OpenAI - just different baseURL.
```

---

## What to expect

Claude will create the API route, Groq client, and results page. Test by submitting the form with a destination like "Tokyo" and budget of $2000 for 5 days. You should see a streaming itinerary appear.

If the Groq call fails, check your API key in `.env.local`.
