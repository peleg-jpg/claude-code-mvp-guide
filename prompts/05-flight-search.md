# Phase 5: Real Flight Search

**Mode: Normal**

**Time: ~15 minutes**

---

## Prompt

```
use context7 for Next.js API routes.

Add real flight search using the Kiwi.com Tequila API:

1. Create /lib/kiwi.ts - Kiwi API client:
   - Base URL: https://api.tequila.kiwi.com
   - API key from env: KIWI_API_KEY (sent as "apikey" header)

2. Create API route /app/api/flights/route.ts that:
   - Accepts: origin city, destination, date_from, date_to, return dates
   - Calls Kiwi search endpoint: GET /v2/search
   - Parameters: fly_from, fly_to, date_from, date_to, curr=USD, limit=10
   - Also does a SECOND search with +/- 3 days flexibility to find cheaper dates
   - Returns sorted results: cheapest first

3. Add a flights section to the trip results page /app/trip/[id]/page.tsx:
   - Flight cards showing: airline, times, stops, price
   - "Cheapest date" highlight badge for flexible search results
   - "Book on Kiwi" button linking to kiwi.com booking page
   - Simple bar chart showing price by date (cheapest dates visualization)

4. Add an interactive map below the flights using Leaflet:
   - npm install leaflet react-leaflet @types/leaflet
   - Show markers for each day's attractions
   - Popup with attraction name and description
   - Use OpenStreetMap tiles (free, no API key)
   - Make the map a Client Component (needs window object)

5. Auto-detect the user's nearest airport using their input city
```

---

## What to expect

The flights section should show real flight data. If Kiwi returns no results, try a popular route like "Tel Aviv to London" with dates 2+ weeks in the future.

The map should show pins for attractions mentioned in the itinerary.
