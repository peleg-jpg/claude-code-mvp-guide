# Phase 3: Scaffold + Core UI

**Mode: Normal**

**Time: ~20 minutes** (this is the biggest phase)

---

## Prompt

```
use context7 for Next.js, Tailwind, and shadcn/ui docs.

Scaffold the project and build the main UI:

1. Create Next.js app: npx create-next-app@latest . --typescript --tailwind --eslint --app --src-dir=false --import-alias="@/*"
2. Install and init shadcn/ui with the "new-york" style
3. Set up Supabase client in /lib/supabase.ts using env vars
4. Create the homepage (/) with a trip input form - ALL in Hebrew:
   - Destination text input with placeholder "לאן טסים?"
   - Budget input in ₪ (ILS) with a reasonable default (e.g., ₪5,000)
   - Number of days slider (1-14 days) - SYNCED with date picker:
     * If user picks start date May 1 and end date May 7 -> slider auto-updates to 7
     * If user changes slider to 5 -> end date auto-updates to May 5
     * Both controls are source of truth - last interaction wins
   - Date range picker (start date + end date) - synced with slider as described above
   - "I'm flexible with dates" toggle - when enabled, replaces exact date picker with a month selector (e.g., "May 2026")
   - A big "תכננו לי טיול" (Plan My Trip) button
5. Style with FULL RTL support:
   - dir="rtl" on html element
   - Dark theme background
   - All labels, placeholders, buttons, and navigation in Hebrew
   - Form layout flows right-to-left
   - Icons and chevrons mirrored for RTL
   - Clean, modern card-based design
   - Mobile responsive
6. Add a top navigation bar with app name in Hebrew and login button placeholder

Use shadcn/ui components: Card, Input, Button, Slider, Label, Switch (for flexible dates toggle).
For the date picker, use a simple date input pair (start + end) if shadcn DatePicker is complex.
```

---

## What to expect

This is the heaviest phase - Claude will create many files. Let it run. When done, start the dev server to check:

```bash
npm run dev
```

Open `http://localhost:3000` and verify:
- Form looks good and is fully in Hebrew
- RTL layout works (text aligned right, form flows right-to-left)
- Days slider and date picker stay in sync when you change either one
- Flexible dates toggle switches between exact dates and month selector
- Budget shows ₪ symbol

If something is off, tell Claude what to fix in the SAME conversation (don't start a new one - that wastes context).
