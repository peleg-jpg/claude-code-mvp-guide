# Phase 4: AI Trip Generation

**Mode: Normal**

**Time: ~15 minutes**

---

## Prompt

```
use context7 for Next.js API routes.

Create the AI trip generation flow:

1. Install the openai npm package: npm install openai
2. Create /lib/openrouter.ts - OpenRouter client using OpenAI SDK:
   - baseURL: "https://openrouter.ai/api/v1"
   - apiKey from env: OPENROUTER_API_KEY
   - Pick any model (e.g., "meta-llama/llama-3.3-70b-instruct", "google/gemini-2.0-flash-exp:free", or any model from openrouter.ai/models)

3. Create API route /app/api/generate-trip/route.ts that:
   - Accepts POST with: destination, budget (₪ ILS), days, startDate, numberOfTravelers, travelerType (solo/couple/family/friends), ageRange, interests (array of selected categories)
   - Calls OpenRouter with a structured prompt asking for a JSON response containing:

     PERSONALIZED ITINERARY:
     - Daily itinerary (morning, afternoon, evening) - in Hebrew
     - Activities TAILORED to the user's selected interests:
       * If they picked "nightlife" - include bars, clubs, rooftop venues in evening slots
       * If they picked "food" - highlight famous restaurants, street food spots, food markets
       * If they picked "nature" - include parks, hikes, scenic viewpoints
       * If they picked "culture" - include museums, historical sites, local experiences
     - Recommendations adjusted for traveler type:
       * Family: kid-friendly activities, family restaurants, stroller-accessible
       * Couple: romantic restaurants, scenic spots, boutique experiences
       * Friends: group activities, nightlife, adventure options
       * Solo: social hostels, walking tours, café culture
     - Recommendations adjusted for age range (e.g., 18-25 gets more nightlife/adventure, 50+ gets more cultural/relaxed)

     FOOD RECOMMENDATIONS:
     - Per day: breakfast, lunch, dinner with ₪ price estimates
     - Tagged by tier: mid-range vs luxurious
     - Matched to user interests (if "food" selected, give more detail)

     TOP ATTRACTIONS:
     - Each with description, average entry cost in ₪, and time needed

     DETAILED COST BREAKDOWN (realistic prices for the destination):
     - All costs calculated for the TOTAL number of travelers, not per person
       * Accommodation - TWO options:
         1. Central/tourist area: per-night rate in ₪, suggest rooms needed for group, total for all nights
         2. Non-central/budget area: same breakdown
       * Food - TWO tiers:
         1. Mid-range: daily cost x travelers x days
         2. Luxurious: daily cost x travelers x days
       * Activities: average daily cost x travelers x days
       * Local transport: daily estimate x travelers x days
     - Total trip cost for each combination (central+mid, central+luxury, budget+mid, budget+luxury)
     - Also include per-person cost for each combination

     TRIP SUMMARY:
     - Total number of attractions/landmarks in the itinerary
     - Top 3-5 must-see highlights
     - Top 3 recommended restaurants
     - Main activities grouped by the user's selected interest categories
     - Trip cost range: cheapest combo to most expensive combo

     LOCAL TIPS:
     - Cultural notes, safety tips, transport tips - in Hebrew

   - Streams the response back to the client

4. Create the results page /app/trip/[id]/page.tsx that displays:
   - TRIP SUMMARY CARD at the top:
     * "X attractions, Y restaurants, Z activities"
     * Top highlights listed
     * Cost range: "₪X - ₪Y for Z travelers"
     * Traveler type and interests reminder
   - Day-by-day cards with morning/afternoon/evening sections
   - Food recommendations with ₪ prices
   - Cost breakdown section showing:
     * Accommodation options side by side (central vs non-central)
     * Food tier comparison (mid-range vs luxurious)
     * Activities average
     * TOTAL for all travelers + per-person breakdown
     * 4 combo options: budget-mid, budget-luxury, central-mid, central-luxury
   - Map section placeholder (we'll add Leaflet next)

5. Connect the form submission (with all fields: destination, budget, days, dates, travelers, type, age, interests) to this API route
6. Show a loading skeleton while generating
7. Store the generated trip in React state for now (we'll save to Supabase in Phase 6 after adding auth)

OpenRouter uses the exact same format as OpenAI - just different baseURL. You can switch models anytime without changing code.
All prices in ₪ (ILS). All costs calculated for the total group, not per person.
The prompt should generate realistic prices for the specific destination.
```

---

## What to expect

Claude will create the API route, OpenRouter client, and results page. Test by submitting the form with:
- Destination: "לונדון" (London)
- Budget: ₪10,000
- 5 days, 2 travelers, couple, 25-35 age range
- Interests: food + attractions

You should see a streaming itinerary that:
- Focuses on food and attractions (your selected interests)
- Suggests romantic spots (couple type)
- Shows a summary card at the top with highlights
- Cost breakdown calculated for 2 people, not 1

If the OpenRouter call fails, check your API key in `.env.local`.
