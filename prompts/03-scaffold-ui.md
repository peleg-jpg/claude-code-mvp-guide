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

   SECTION 1 - Destination & Budget:
   - Destination text input with placeholder "לאן טסים?"
   - Budget input in ₪ (ILS) with a reasonable default (e.g., ₪5,000)

   SECTION 2 - Travelers:
   - Number of travelers: number input (1-10), default 2
   - Traveler type: radio/select - יחיד (solo), זוג (couple), משפחה (family with kids), חברים (friends group)
   - Age range: select - 18-25, 25-35, 35-50, 50+, גילאים מעורבים (mixed)

   SECTION 3 - What do you want to do? (Interest survey):
   - Multi-select checkboxes, pick 1-4:
     * אטרקציות ואתרים (Attractions & landmarks)
     * חיי לילה (Nightlife & bars)
     * אוכל ומסעדות (Food & restaurants)
     * טבע וטיולים (Nature & hiking)
     * קניות (Shopping)
     * תרבות ומוזיאונים (Culture & museums)
     * חוף וים (Beach & relaxation)
     * אקסטרים והרפתקאות (Adventure & extreme sports)
   - Limit to max 4 selections, show a note "בחרו עד 4"

   SECTION 4 - Dates & Duration:
   - Number of days slider (1-14 days) - SYNCED with date picker:
     * If user picks start May 1, end May 7 -> slider auto-updates to 7
     * If user changes slider to 13 -> end date MUST change to May 13
     * If user changes start date -> end date adjusts to keep same days
     * CRITICAL: use startDate + days as source of truth. Derive endDate = startDate + days.
       When user changes endDate, recalculate days = endDate - startDate.
       Every change to either control immediately updates the other.
   - Date range picker (start date + end date)
   - "תאריכים גמישים" (Flexible dates) toggle:
     * When ON: hide exact date pickers, show a month selector dropdown instead
     * Month options: next 6 months from today

   - A big "תכננו לי טיול" (Plan My Trip) button

5. Style with FULL RTL support:
   - dir="rtl" on html element
   - Dark theme background
   - All labels, placeholders, buttons, and navigation in Hebrew
   - Form layout flows right-to-left
   - Icons and chevrons mirrored for RTL
   - Clean, modern card-based design with clear section separators
   - Mobile responsive - sections stack vertically on mobile
6. Add a top navigation bar with app name in Hebrew and login button placeholder

Use shadcn/ui components: Card, Input, Button, Slider, Label, Switch, Checkbox, Select, RadioGroup.
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
- **Days slider and date picker stay in sync** - change slider to 13, dates must update. Change dates to a 5-day range, slider must update to 5. No conflicts.
- Flexible dates toggle switches between exact dates and month selector
- Traveler section shows count, type, and age range
- Interest checkboxes work (max 4)
- Budget shows ₪ symbol

If something is off, tell Claude what to fix in the SAME conversation (don't start a new one - that wastes context).
