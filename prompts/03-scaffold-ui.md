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
4. Create the homepage (/) with a trip input form:
   - Destination text input with placeholder "Where do you want to go?"
   - Budget input in USD with a reasonable default (e.g., $1000)
   - Number of days slider (1-14 days)
   - Date range picker for travel dates
   - A big "Plan My Trip" button
5. Style it with:
   - Dark theme background
   - Hebrew RTL layout (dir="rtl" on html)
   - Clean, modern card-based design
   - Mobile responsive
6. Add a top navigation bar with app name and login button placeholder

Use shadcn/ui components: Card, Input, Button, Slider, Label.
For the date picker, use a simple date input if shadcn DatePicker is complex.
```

---

## What to expect

This is the heaviest phase - Claude will create many files. Let it run. When done, start the dev server to check:

```bash
npm run dev
```

Open `http://localhost:3000` and verify the form looks good. If something is off, tell Claude what to fix in the SAME conversation (don't start a new one - that wastes context).
