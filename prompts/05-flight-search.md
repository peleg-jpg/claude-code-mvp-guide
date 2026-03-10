# Phase 5: Real Flight Search

**Mode: Normal**

**Time: ~15 minutes**

---

## Prompt

```
use context7 for Next.js API routes, Leaflet, and react-leaflet.

Add real flight search using SerpAPI Google Flights:

1. Create /lib/serpapi.ts - SerpAPI client:
   - Endpoint: https://serpapi.com/search.json
   - API key from env: SERPAPI_KEY
   - Engine: google_flights

2. Create API route /app/api/flights/route.ts that:
   - Accepts: origin (IATA code), destination (IATA code), outbound_date, return_date, currency=ILS, numberOfTravelers, flexibleMonth (optional - e.g., "2026-08" for August)
   - For EXACT dates mode:
     * Search SerpAPI with specific outbound_date and return_date
     * Also search +/- 3 days to show nearby cheaper options
     * Multiply per-person price by numberOfTravelers for total
   - For FLEXIBLE dates mode:
     * CRITICAL: Only search within the selected month. If user picked August, NEVER return June or July flights.
     * Search multiple date ranges within the month (e.g., departing each Monday of the month)
     * Group results by WEEK within the month:
       - "שבוע 1 (1-7 אוגוסט): ממוצע ₪X לאדם" (Week 1: avg ₪X per person)
       - "שבוע 2 (8-14 אוגוסט): ממוצע ₪Y לאדם" (Week 2: avg ₪Y per person)
       - "שבוע 3 (15-21 אוגוסט): ממוצע ₪Z לאדם"
       - "שבוע 4 (22-31 אוגוסט): ממוצע ₪W לאדם"
     * Highlight the cheapest week prominently
     * Within each week, show the 2-3 cheapest specific departure dates
     * Show both per-person AND total group price (x numberOfTravelers)
   - Returns results sorted by price (cheapest first)
   - All prices in ₪

3. Create a city-to-IATA mapping helper:
   - Common Israeli airports: TLV (Ben Gurion), ETH (Eilat)
   - Map destination city names to IATA codes (use Groq if needed for uncommon cities)

4. Add a flights section to the trip results page /app/trip/[id]/page.tsx:
   - For exact dates:
     * Flight cards showing: airline, departure/arrival times, stops, price per person in ₪, total for group
     * "Cheapest nearby date" badge for +/- 3 day results
   - For flexible dates:
     * Weekly summary cards: week range, average price, cheapest date in that week
     * Cheapest week highlighted in green
     * Within each week: expandable list of 2-3 best options
     * "Select this week" button that switches to exact dates mode with those dates
   - "Book" button linking to Google Flights booking page
   - All text in Hebrew
   - Show "₪X per person | ₪Y total for Z travelers" format

5. Add an interactive map below the flights using Leaflet:
   - npm install leaflet react-leaflet @types/leaflet
   - Show markers for each day's attractions from the itinerary
   - Popup with attraction name and description in Hebrew
   - Use OpenStreetMap tiles (free, no API key)
   - Make the map a Client Component (needs window object)

6. Auto-detect origin airport - default to TLV (Ben Gurion) for Israeli users

Note: SerpAPI free tier gives 100 searches/month. For flexible dates, batch searches efficiently - 4 searches per month (one per week) instead of 30 (one per day).
```

---

## What to expect

The flights section should show real Google Flights data with prices in ₪.

**Exact dates test:** Search TLV to London with specific dates 2+ weeks out. Should show flight cards with per-person and total group price.

**Flexible dates test:** Pick "August 2026" as flexible month. Should see:
- 4 weekly summaries with average prices (ONLY August dates, never other months)
- Cheapest week highlighted
- Expandable options within each week
- Prices shown for your group size

The map should show pins for attractions mentioned in the itinerary.

**SerpAPI tip:** If you hit the 100 search limit during development, cache results in a JSON file for testing. For flexible months, you only need 4-5 searches per month (not 30).
