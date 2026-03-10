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
   - Accepts: origin (IATA code), destination (IATA code), outbound_date, return_date, currency=ILS
   - Calls SerpAPI with engine=google_flights parameters:
     * departure_id (origin IATA), arrival_id (destination IATA)
     * outbound_date, return_date, currency=ILS, hl=he (Hebrew)
   - If "flexible dates" mode is on:
     * Make multiple searches across the selected month (e.g., every few days in May)
     * Or use SerpAPI's date range to find cheapest departure dates
     * Return a price calendar showing flight cost per date
   - Returns results sorted by price (cheapest first)
   - Convert/display all prices in ₪

3. Create a city-to-IATA mapping helper:
   - Common Israeli airports: TLV (Ben Gurion), ETH (Eilat)
   - Map destination city names to IATA codes (use Groq if needed for uncommon cities)

4. Add a flights section to the trip results page /app/trip/[id]/page.tsx:
   - Flight cards showing: airline, departure/arrival times, stops, price in ₪
   - "Cheapest date" highlight badge for flexible search results
   - If flexible dates: show a visual price calendar/chart for the month
     * Bar chart or grid showing price per date
     * Highlight the cheapest dates in green
     * Let user click a date to select it
   - "Book" button linking to Google Flights booking page
   - All text in Hebrew

5. Add an interactive map below the flights using Leaflet:
   - npm install leaflet react-leaflet @types/leaflet
   - Show markers for each day's attractions from the itinerary
   - Popup with attraction name and description in Hebrew
   - Use OpenStreetMap tiles (free, no API key)
   - Make the map a Client Component (needs window object)

6. Auto-detect origin airport - default to TLV (Ben Gurion) for Israeli users

Note: SerpAPI free tier gives 100 searches/month - more than enough for development and demo.
```

---

## What to expect

The flights section should show real Google Flights data with prices in ₪. Test with a popular route like TLV to London with dates 2+ weeks in the future.

If using flexible dates, you should see a price calendar showing which dates are cheapest to fly.

The map should show pins for attractions mentioned in the itinerary.

**SerpAPI tip:** If you hit the 100 search limit during development, cache results in a JSON file for testing.
