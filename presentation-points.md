# claude-code-mvp-guide - What's Taught Inside

**Purpose**: Structured list of everything taught in the guide, with Hebrew summaries and links. For building a Hebrew live webinar presentation.

---

## 1. The Big Promise - MVP in 2 Hours for $20

**תקציר**: המדריך מלמד איך לבנות אפליקציה שלמה ומוכנה לפרודקשן תוך שעתיים עם קלוד קוד, בעלות של 20 דולר בלבד. כל השירותים חינמיים חוץ מהמנוי לקלוד.

- Build a deployed, production-ready web app using Claude Code in ~2 hours
- Total cost: $20 (Claude Pro subscription only) - every other service is free tier
- The app built: trip planner with AI itineraries, real flight prices, interactive maps, user auth, Hebrew RTL UI
- End result: a live URL on Vercel you can share
- Not a toy demo - real APIs, real data, real users

---

## 2. CLAUDE.md - The Rules File

**תקציר**: קובץ הוראות שנטען בכל פרומפט. מונע מקלוד לנחש לא נכון ומחסך 3-5 דולר בקרדיטים מבוזבזים.

- A markdown file in your project root that loads into every Claude Code prompt automatically
- Tells Claude: what tech stack you use, coding style, naming conventions, project structure
- Prevents wrong guesses and wasted credits from corrections
- The guide provides a pre-written CLAUDE.md template to copy
- **This is the single most impactful thing beginners skip** - and the first thing pros set up

---

## 3. Plan Mode

**תקציר**: מצב תכנון בקלוד קוד - קלוד קורא וחושב בלי לכתוב קוד, כמעט בחינם. מתכננים את כל הארכיטקטורה לפני שמתחילים לבנות.

- Toggle with **Shift+Tab** keyboard shortcut
- Claude reads and thinks but doesn't write code - nearly free (minimal credit usage)
- You describe what to build, Claude designs: database schema, page structure, component tree, API routes, data flow
- **Switch to Opus model** (`/model opus`) for planning - smarter for architecture decisions, and since planning uses few tokens the higher per-token cost barely matters
- Exit Plan Mode (Shift+Tab again) then `/model sonnet` for building
- Saves $3-5 per project by avoiding building the wrong thing

---

## 4. Model Switching (Opus vs Sonnet)

**תקציר**: שימוש במודל חזק יותר (Opus) לתכנון ובמודל זול יותר (Sonnet) לבנייה. החלפה בפקודה פשוטה.

- `/model opus` - stronger model for architecture planning, complex decisions
- `/model sonnet` - cheaper model for writing code, building features
- Planning uses few tokens so Opus cost is negligible
- Building uses many tokens so Sonnet saves significantly
- Saves $3-5 per project

---

## 5. MCPs (Model Context Protocol)

**תקציר**: תוספים שנותנים לקלוד יכולות על - גישה לדוקומנטציה עדכנית, ניהול מסד נתונים ישיר, ושליטה בדפדפן לבדיקות ויזואליות.

### 5a. Context7 MCP
- **מה זה**: שולף דוקומנטציה עדכנית של כל ספריה/פריימוורק בזמן אמת
- Prevents Claude from hallucinating API methods or using outdated syntax
- Usage: add "use context7" to your prompts when working with frameworks
- Saves $2-5 per project in debugging wrong API calls
- **Install**: `claude mcp add context7 -- npx -y @upstash/context7-mcp@latest`
- Link: https://github.com/nichochar/context7

### 5b. Supabase MCP
- **מה זה**: קלוד מנהל את מסד הנתונים ישירות - יוצר טבלאות, כותב SQL, מגדיר הרשאות
- No need to manually write SQL in the Supabase dashboard
- Claude executes SQL directly through the MCP
- **Install**: `claude mcp add supabase -- npx -y @supabase/mcp-server-supabase@latest --project-ref YOUR_PROJECT_REF`
- Find project ref in URL: `https://supabase.com/dashboard/project/YOUR_PROJECT_REF`
- First run opens browser for OAuth login
- Optional: add `--read-only` flag for safety
- Link: https://supabase.com/docs/guides/getting-started/mcp

### 5c. Playwright MCP
- **מה זה**: קלוד שולט בדפדפן, מצלם מסך, ורואה איך האפליקציה נראית בפועל
- Used for visual QA in Phase 8 - cheaper than describing UI problems in words
- Claude navigates to your app, screenshots at different screen sizes, spots issues, fixes them
- **Install**: `claude mcp add playwright -- npx -y @anthropic-ai/mcp-server-playwright`
- Link: https://github.com/anthropics/mcp-server-playwright

---

## 6. Skills System

**תקציר**: הוראות מוכנות מראש שקלוד עוקב אחריהן - כמו להגיד למעצב "תעקוב אחרי הסטייל גייד הזה". מותקנות בפקודה פשוטה.

### 6a. frontend-design skill
- **מה זה**: כללי עיצוב UI מקצועיים - ריווח, צבעים, רספונסיביות, היררכיית קומפוננטות
- ROI: 3-5x return in design quality
- **Install**: `claude install-skill anthropics/frontend-design`

### 6b. find-skills skill
- **מה זה**: מטא-סקיל שעוזר למצוא סקילים אחרים שימושיים
- Near-zero cost to use
- **Install**: `claude install-skill vercel-labs/find-skills`

### 6c. vercel-react-best-practices skill
- **מה זה**: פטרנים של React ו-Next.js - Server Components, Client Components, data fetching
- Adds ~1000 tokens of context per prompt
- **Install**: `claude install-skill vercel-labs/vercel-react-best-practices`

### 6d. skill-creator (project #3+)
- **מה זה**: ליצור סקילים מותאמים אישית שמקפסלים פטרנים חוזרים שלך

---

## 7. What to Skip (and Why)

**תקציר**: לא כל MCP או סקיל שווה להתקין. המדריך מלמד מה לדלג כדי לא לבזבז טוקנים וקרדיטים.

### MCPs to skip for first project:
- Obsidian, Figma, Linear, GitHub Issues, Firecrawl, Vercel MCP, extra search MCPs
- Each MCP adds 500-2000 tokens to EVERY prompt - unnecessary ones waste money

### Skills to skip for first project:
- skill-creator (learn patterns first)
- systematic-debugging (Playwright screenshots usually enough)
- TDD (adds 40% time)
- code-review, security, SEO/marketing skills (not for MVP)

---

## 8. Sound Notifications Setup

**תקציר**: הגדרה שקלוד משמיע צליל כשהוא מסיים משימה - אפשר ללכת להכין קפה ולחזור כשהוא מוכן.

- Claude plays a sound when it finishes a task
- Configured in `.claude/settings.json`
- **macOS**: `afplay /System/Library/Sounds/Glass.aiff` (also: `Funk.aiff`, `Hero.aiff`, `Submarine.aiff`)
- **Linux**: replace `afplay` with `paplay`
- **Windows WSL**: `powershell.exe -c '(New-Object Media.SoundPlayer "C:\\Windows\\Media\\notify.wav").PlaySync()'`
- The guide provides a pre-configured settings.json

---

## 9. VS Code RTL Extension

**תקציר**: תוסף ל-VS Code שמסדר את התצוגה של טקסט עברי/ערבי בפאנל הצ'אט של קלוד קוד. לא קשור לאפליקציה עצמה.

- Extension: `rtl-for-vs-code-agents` by GuyRonnen
- **Install**: `code --install-extension GuyRonnen.rtl-for-vs-code-agents`
- Fixes Hebrew/Arabic text display in Claude Code's chat panel in VS Code
- Has nothing to do with the app's RTL - that's handled by code
- Link: https://github.com/GuyRonnen/rtl-for-vs-code-agents

---

## 10. The Tech Stack - All Free or Cheap

**תקציר**: כל הטכנולוגיות נבחרו בכוונה כי הן חינמיות או עם תוכנית חינמית נדיבה.

| Tech | What It Does | Cost | Link |
|------|-------------|------|------|
| **Next.js 15** | Full-stack React framework (App Router) | Free | https://nextjs.org |
| **Tailwind CSS** | Utility-first CSS framework | Free | https://tailwindcss.com |
| **shadcn/ui** | Pre-built components (style: "new-york") | Free | https://ui.shadcn.com |
| **Supabase** | PostgreSQL database + auth + RLS | Free tier | https://supabase.com |
| **OpenRouter** | Access to 100+ LLM models via one API (OpenAI-compatible) | Free tier + pay-per-use | https://openrouter.ai |
| **SerpAPI** | Real Google Flights prices | 100 free searches/month | https://serpapi.com |
| **Leaflet** | Interactive maps | Free, no API key | https://leafletjs.com |
| **OpenStreetMap** | Map tiles (used with Leaflet) | Free | https://www.openstreetmap.org |
| **Vercel** | Hosting + deployment | Free tier | https://vercel.com |
| **GitHub** | Code repository | Free | https://github.com |
| **Claude Pro** | AI coding assistant | $20/month | https://claude.ai |

---

## 11. The 8 Build Phases

### Phase 0: Setup (15 min, no credits used)
**תקציר**: כל ההכנה לפני שמתחילים - יצירת חשבונות, התקנת כלים, העתקת קבצי תצורה. לא צורך קרדיטים.

- Create accounts: Claude Pro, Supabase, OpenRouter, SerpAPI, Vercel, GitHub
- Install: Node.js 18+, VS Code, Vercel CLI (`npm i -g vercel`), Claude Code (`curl https://code.claude.ai/install.sh | sh`)
- Login: `claude` then `/login`
- Install 3 MCPs (Context7, Supabase, Playwright)
- Install 3 skills (frontend-design, find-skills, vercel-react-best-practices)
- Copy from guide repo: CLAUDE.md, .env.example -> .env.local, .claude/settings.json
- Optional: VS Code RTL extension

### Phase 1: Architecture Planning (10 min)
**תקציר**: Plan Mode - קלוד מתכנן את כל הארכיטקטורה: סכמת מסד נתונים, API routes, מבנה עמודים, עץ קומפוננטות. כמעט בחינם.

- Enter Plan Mode (Shift+Tab), switch to Opus (`/model opus`)
- Claude designs: database schema (trips, itinerary_days, saved_flights), API routes (/api/generate-trip, /api/flights), page structure (/, /trip/[id], /my-trips), component tree, data flow diagram
- Client vs Server Components decisions
- Exit Plan Mode (Shift+Tab), switch to Sonnet (`/model sonnet`)

### Phase 2: Database Setup (5 min)
**תקציר**: קלוד יוצר את הטבלאות ב-Supabase דרך ה-MCP ישירות - בלי לגעת בדשבורד. כולל הגדרת Row Level Security.

- Claude creates 3 tables via Supabase MCP: `trips`, `itinerary_days`, `saved_flights`
- JSONB columns for flexible data (itinerary plans, flight results)
- Row Level Security (RLS): users see only their own data, public trips via share URL
- Tables may have 5-10 second delay before showing in dashboard

### Phase 3: Scaffold UI + Form (20 min - biggest phase)
**תקציר**: הפאזה הגדולה ביותר - בניית שלד Next.js עם טופס קלט מלא בעברית, כולל סנכרון חכם של תאריכים ו-RTL מושלם.

- Scaffold: `npx create-next-app@latest . --typescript --tailwind --eslint --app --src-dir=false --import-alias="@/*"`
- shadcn/ui: style "new-york", components: Card, Input, Button, Slider, Label, Switch, Checkbox, Select, RadioGroup
- Supabase client setup: `/lib/supabase.ts`
- **Full Hebrew RTL form** with sections:
  - Destination & budget (in ₪)
  - Travelers: count (1-10), type (solo/couple/family/friends), age range
  - Interests: 8 categories, max 4 selectable
  - **Smart date sync**: days slider + date picker stay perfectly synced (single source of truth: startDate + days)
  - **Flexible dates toggle**: switches to month picker instead of exact dates
- `dir="rtl"` on html element, all text/labels/buttons in Hebrew
- Navigation bar with login button placeholder

### Phase 4: AI Trip Generation (15 min)
**תקציר**: חיבור ל-OpenRouter API ליצירת מסלול מותאם אישית עם AI. כולל הנדסת פרומפט לקבלת JSON מובנה. OpenRouter נותן גישה ליותר מ-100 מודלים דרך API אחד.

- Install: `npm install openai` (OpenRouter uses OpenAI-compatible format)
- OpenRouter setup: baseURL `https://openrouter.ai/api/v1`, pick any model (Llama, Claude, GPT, Mistral, etc.)
- **The key concept**: any OpenAI-compatible LLM provider works with the same code - just change the baseURL and API key. OpenRouter gives you access to 100+ models through one API.
- Link: https://openrouter.ai
- **API route `/api/generate-trip`** accepts: destination, budget (₪), days, travelers, type, age, interests
- **Prompt engineering** for structured JSON output:
  - Day-by-day itinerary (morning, afternoon, evening) personalized by interests + traveler type + age
  - Food recommendations per day (mid-range vs luxury) with ₪ prices
  - Top attractions with entry cost and time needed
  - **Detailed cost breakdown**: accommodation (central vs non-central) x food (mid vs luxury) = 4 combinations, ALL for full group not per-person
  - Trip summary card + local tips
- **Results page** `/trip/[id]`: summary card, day cards, food recs, cost breakdown, map placeholder
- Streaming responses for real-time display

### Phase 5: Real Flights + Maps (15 min)
**תקציר**: חיפוש טיסות אמיתיות מ-Google Flights דרך SerpAPI, ומפה אינטראקטיבית עם סיכות לכל אטרקציה.

- SerpAPI setup: engine `google_flights`, currency ILS
- **Two flight search modes:**
  - **Exact dates**: search with +/- 3 day alternatives
  - **Flexible dates**: grouped by WEEK within selected month only (never cross month boundaries!), highlight cheapest week, show 2-3 cheapest per week
- Prices always: ₪ per person + ₪ total for group
- City-to-IATA mapping: TLV (Ben Gurion), ETH (Eilat), LLM for uncommon cities
- Default origin: TLV for Israeli users
- **SerpAPI free tier**: 100 searches/month - batch 4 per flexible month, not 30
- **Leaflet map**: `npm install leaflet react-leaflet @types/leaflet`
  - Client Component (needs `window`)
  - Markers for each day's attractions, Hebrew popups
  - OpenStreetMap tiles (free, no API key)
- Link (SerpAPI): https://serpapi.com
- Link (Leaflet): https://leafletjs.com

### Phase 6: Authentication + Saving (10 min)
**תקציר**: הוספת אימות משתמשים (אימייל + Google) ושמירת טיולים - 10 דקות בזכות Supabase Auth.

- Install: `npm install @supabase/ssr`
- Supabase Auth: email/password + Google OAuth
- Auth middleware for Next.js App Router
- Login/signup modal: shadcn Dialog + Tabs (Login | Sign Up)
- Google OAuth: requires Google Cloud OAuth client ID in Supabase Dashboard > Authentication > Providers
- "Save Trip" button: triggers login if not authenticated, saves to Supabase
- `/my-trips` protected page: list saved trips, delete option
- Share: copy public URL, works without login (`is_public=true`)
- Link (Supabase Auth): https://supabase.com/auth

### Phase 7: Polish + Deploy (15 min)
**תקציר**: ליטוש אחרון - loading states, טיפול בשגיאות, meta tags - ואז דפלוי לVercel. מ-localhost ל-URL חי בדקות.

- Loading: skeleton screens, spinners, button loading states
- Error: user-friendly messages for LLM API failures, empty flight results, network errors
- Meta tags: dynamic OG title/description for social sharing
- Responsive: cards stack on mobile, expandable map
- Build: `npm run build` to catch TypeScript errors, hydration mismatches
- Deploy:
  ```
  git init && git add -A && git commit -m "Trip planner MVP"
  # Push to GitHub
  vercel deploy
  ```
- Set env vars in Vercel Dashboard > Settings > Environment Variables
- Link (Vercel): https://vercel.com

### Phase 8: Visual QA with Playwright (5 min)
**תקציר**: קלוד פותח את האפליקציה בדפדפן, מצלם מסך בגדלים שונים, מזהה בעיות ויזואליות ומתקן אותן ישירות.

- Claude uses Playwright MCP to open the app in a browser
- Screenshots: main form, filled form, loading state, results, flights, mobile (375px)
- Spots: broken layouts, overlapping text, missing elements
- Fixes issues directly
- Cheaper than describing visual problems in chat

---

## 12. Credit-Saving Tips (8 Rules)

**תקציר**: 8 כללים שמחסכים 16-32 דולר לפרויקט. ההבדל בין לרוקן את הקרדיטים ביום לבין לעבוד שבוע שלם.

1. **CLAUDE.md first** / **כתוב CLAUDE.md לפני הפרומפט הראשון** - saves $3-5/project
2. **Plan Mode before Build Mode** / **Plan Mode לפני שכותבים שורת קוד** - saves $3-5/project
3. **One big prompt > many small ones** / **פרומפט אחד גדול עדיף על הרבה קטנים** - saves $2-4/session (context history compounds cost)
4. **Always say "use context7"** / **תמיד תגיד use context7** - saves $2-5/project (prevents hallucinated APIs)
5. **Don't install unnecessary MCPs** / **אל תתקין MCPs מיותרים** - saves $1-3/session (each adds 500-2000 tokens per prompt)
6. **Verify with screenshots, not words** / **תוודא עם צילומי מסך, לא עם מילים** - saves $1-3/fix
7. **Use /compact for long conversations** / **השתמש ב-/compact כשהשיחה מתארכת** - saves $1-2/session
8. **Opus for planning, Sonnet for building** / **Opus לתכנון, Sonnet לבנייה** - saves $3-5/project

**Total: $16-32 savings per project**

---

## 13. Key Commands & Keyboard Shortcuts

**תקציר**: הפקודות וקיצורי המקשים הכי חשובים שלומדים במדריך.

| Command / Shortcut | What It Does |
|---|---|
| `Shift+Tab` | Toggle Plan Mode (enter/exit) |
| `/model opus` | Switch to Opus model (for planning) |
| `/model sonnet` | Switch to Sonnet model (for building) |
| `/compact` | Compress conversation history (save tokens) |
| `/login` | Login to Claude Code |
| `claude mcp add ...` | Install an MCP |
| `claude install-skill ...` | Install a skill |

---

## 14. Development Concepts Taught

**תקציר**: מושגי פיתוח שלומדים תוך כדי הבנייה - לא בתיאוריה, אלא בפרקטיקה.

- **Server vs Client Components** / **קומפוננטות שרת מול קליינט** - Next.js App Router pattern, when to use `"use client"`
- **Database schema design** / **תכנון סכמת מסד נתונים** - tables, relationships, JSONB for flexible data
- **Row Level Security (RLS)** / **אבטחה ברמת שורה** - users only see their own data at database level
- **API routes** / **נתיבי API** - Next.js route handlers (`/api/generate-trip`, `/api/flights`)
- **Streaming AI responses** / **תגובות AI בזמן אמת** - show results as they generate, not after
- **Prompt engineering** / **הנדסת פרומפט** - getting structured JSON from an LLM (OpenRouter)
- **OpenAI SDK with non-OpenAI providers** / **SDK של OpenAI עם ספקים אחרים** - same code format, just change baseURL (OpenRouter, or any compatible provider)
- **RTL layout** / **ממשק מימין לשמאל** - Hebrew right-to-left from day one
- **Form state synchronization** / **סנכרון מצב טופס** - synced slider + date picker
- **OAuth flow** / **תהליך אימות OAuth** - Google login through Supabase
- **Environment variables** / **משתני סביבה** - .env.local locally, Vercel dashboard for production
- **Git + GitHub + Vercel pipeline** / **צנרת דפלוי** - code to live URL
- **OG meta tags** / **תגיות לשיתוף ברשתות** - dynamic sharing previews

---

## 15. Environment Variables

**תקציר**: 4 מפתחות API שצריך להגדיר. הכל חינם חוץ מקלוד.

| Variable | Where to Get | Link |
|----------|-------------|------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase Dashboard > Settings > API | https://supabase.com/dashboard |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase Dashboard > Settings > API | https://supabase.com/dashboard |
| `OPENROUTER_API_KEY` | OpenRouter Dashboard > API Keys | https://openrouter.ai/keys |
| `SERPAPI_KEY` | SerpAPI Dashboard (100 free/month) | https://serpapi.com/manage-api-key |

---

## 16. What Gets Built - The Final App

**תקציר**: מה המשתמש מקבל בסוף - אפליקציה שלמה עם AI, טיסות אמיתיות, מפה, אימות משתמשים, ושיתוף.

1. Landing page with Hebrew RTL trip input form
2. Smart date sync (slider + date picker stay in perfect sync)
3. Flexible dates mode (pick whole month)
4. Traveler preferences: count, type (solo/couple/family/friends), age range, interests (8 categories)
5. AI-generated daily itinerary personalized by preferences (OpenRouter)
6. Trip summary card (attractions, highlights, restaurants, cost range)
7. Real flight search with live Google Flights prices (SerpAPI)
8. Flexible date flight grouping by week with cheapest week highlight
9. Interactive map with attraction markers (Leaflet + OpenStreetMap)
10. Full cost breakdown: 4 combinations (accommodation x food tier), per-person AND total group
11. User auth: email + Google OAuth (Supabase Auth)
12. Save trips to account
13. Share trips via public URL
14. Mobile responsive
15. Dark theme
16. Deployed on Vercel with live URL
17. All prices in ₪ (Israeli Shekels)

---

## 17. Progression Path After the Guide

**תקציר**: מה עושים אחרי שסיימו את הפרויקט הראשון - התקדמות מפרויקט #1 ל-#2 ל-#3+.

- **Project #1** (this guide): Learn the basics, build with the 8-phase framework
- **Project #2+**: Create custom skills with skill-creator
  - Package your repeated patterns into reusable instructions
- **Extend the trip planner** (30-min sessions each):
  - Hotel search (Booking.com/Airbnb API)
  - Weather forecast (OpenWeather free API)
  - Budget tracking during trip
  - Multi-language (English/Hebrew toggle)
  - PDF export
  - Social sharing with OG images

---

## 18. The Underlying Philosophy

**תקציר**: הגישה שעומדת מאחורי המדריך - לא רק מה לבנות, אלא איך לחשוב.

- **Start with Plan Mode, not code** / **תתכנן לפני שתכתוב** - architecture decisions should be cheap
- **Use free/cheap services** / **תשתמש בשירותים חינמיים** - no reason to pay for what you can get free
- **CLAUDE.md before coding** / **תכתוב CLAUDE.md לפני הכל** - prevents repeated mistakes
- **Context7 for every framework** / **context7 לכל ספריה** - use current docs, not training data
- **Hebrew as first-class** / **עברית מהשלב הראשון** - RTL from Phase 3, not an afterthought
- **Real data, not mocks** / **נתונים אמיתיים, לא מזויפים** - actual flight prices, not fake data
- **Mobile-first** / **מובייל קודם** - responsive from the start
- **Screenshot-based QA** / **בדיקות ויזואליות** - visual testing beats verbal descriptions
- **Phase-based development** / **בנייה בשלבים** - 8 focused phases, each with clear deliverables

---

## All Links in One Place

**תקציר**: כל הלינקים ממוקמים כאן למען הנוחות - להעתקה ל-Google Docs.

### Services & Accounts
| Service | URL |
|---------|-----|
| Claude Pro | https://claude.ai |
| Claude Code Install | https://code.claude.ai/install.sh |
| Supabase | https://supabase.com |
| Supabase Dashboard | https://supabase.com/dashboard |
| Supabase MCP Docs | https://supabase.com/docs/guides/getting-started/mcp |
| Supabase Auth | https://supabase.com/auth |
| OpenRouter | https://openrouter.ai |
| OpenRouter API Keys | https://openrouter.ai/keys |
| SerpAPI | https://serpapi.com |
| SerpAPI API Key | https://serpapi.com/manage-api-key |
| Vercel | https://vercel.com |
| GitHub | https://github.com |

### Frameworks & Libraries
| Library | URL |
|---------|-----|
| Next.js | https://nextjs.org |
| Tailwind CSS | https://tailwindcss.com |
| shadcn/ui | https://ui.shadcn.com |
| Leaflet | https://leafletjs.com |
| OpenStreetMap | https://www.openstreetmap.org |

### Claude Code Tools
| Tool | URL |
|------|-----|
| Context7 MCP | https://github.com/nichochar/context7 |
| Playwright MCP | https://github.com/anthropics/mcp-server-playwright |
| VS Code RTL Extension | https://github.com/GuyRonnen/rtl-for-vs-code-agents |

---

## Summary Count: 44 Things You Learn

1. Plan Mode, 2. CLAUDE.md, 3. Model switching (Opus/Sonnet), 4. /compact, 5. Context7 MCP, 6. Supabase MCP, 7. Playwright MCP, 8. Skills system, 9. frontend-design skill, 10. find-skills skill, 11. vercel-react-best-practices skill, 12. What to skip (MCPs/skills), 13. Sound notifications, 14. VS Code RTL extension, 15. Next.js 15 App Router, 16. Tailwind CSS, 17. shadcn/ui, 18. Supabase (database), 19. Supabase Auth (email + OAuth), 20. Row Level Security, 21. OpenRouter (LLM API), 22. OpenAI SDK with non-OpenAI providers, 23. Prompt engineering for JSON, 24. Streaming responses, 25. SerpAPI (Google Flights), 26. Flexible date search, 27. Leaflet maps, 28. RTL layout (Hebrew), 29. Form state sync, 30. Server vs Client Components, 31. API routes, 32. Protected routes + middleware, 33. Environment variables, 34. Git workflow, 35. GitHub, 36. Vercel deployment, 37. OG meta tags, 38. Mobile responsive design, 39. Visual QA with Playwright, 40. Credit optimization (8 rules), 41. Phase-based development, 42. Cost breakdown ($20 total), 43. Custom skills (project #2+), 44. Extension path (hotel, weather, PDF, etc.)
