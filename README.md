# Build & Deploy an MVP in 2 Hours with Claude Code ($20 Total)

A step-by-step guide for first-time Claude Code users to build a real, deployed app from scratch.

**What you'll build:** A trip planner where users enter a destination, budget, and travel dates - and get a full daily itinerary with food, attractions, tips, AND real flight search with flexible date pricing. Deployed on Vercel, looks like a real app.

**Total cost: $20** (Claude Pro subscription). Everything else is free.

**Time: ~2 hours** from zero to deployed.

---

## What's in This Repo

```
claude-code-mvp-guide/
├── README.md              ← You are here
├── CLAUDE.md              ← Drop this into your project (critical!)
├── .env.example           ← All API keys you need
├── prompts/               ← Copy-paste prompts for each phase
│   ├── 01-plan.md
│   ├── 02-database.md
│   ├── 03-scaffold-ui.md
│   ├── 04-trip-generation.md
│   ├── 05-flight-search.md
│   ├── 06-auth-save.md
│   ├── 07-polish-deploy.md
│   └── 08-visual-check.md
└── docs/
    ├── credit-tips.md     ← How to save money
    ├── skills-guide.md    ← Which skills to install (and which to skip)
    └── next-steps.md      ← What to learn after your first MVP
```

---

## Prerequisites

- A computer with a terminal (Mac, Linux, or WSL on Windows)
- [Node.js 18+](https://nodejs.org/) installed
- [VS Code](https://code.visualstudio.com/) installed
- [Vercel CLI](https://vercel.com/docs/cli): `npm i -g vercel`
- A GitHub account (for deployment)
- $20 for a Claude Pro subscription

---

## Phase 0: Setup (15 minutes, no credits used)

### Step 1: Get Your Accounts (all free)

| Service | URL | What You Need |
|---------|-----|---------------|
| **Claude Pro** | [claude.ai](https://claude.ai) | $20/month subscription |
| **Supabase** | [supabase.com](https://supabase.com) | Free account + new project |
| **Groq** | [console.groq.com](https://console.groq.com) | Free API key (no credit card) |
| **Kiwi.com Tequila** | [tequila.kiwi.com](https://tequila.kiwi.com) | Free API key for flight search |
| **Vercel** | [vercel.com](https://vercel.com) | Free account (connect GitHub) |

### Step 2: Install Claude Code

```bash
curl https://code.claude.ai/install.sh | sh
```

Then login:
```bash
claude
/login
```

### Step 3: Install VS Code RTL Extension (for Hebrew users)

If you'll be working with Hebrew text, install the RTL extension:

```bash
code --install-extension GuyRonnen.rtl-for-vs-code-agents
```

Or search "rtl-for-vs-code-agents" in the VS Code Extensions panel. [GitHub](https://github.com/GuyRonnen/rtl-for-vs-code-agents)

- Fixes Hebrew/Arabic display in Claude Code chat
- Zero performance cost - pure display fix

### Step 4: Install MCPs (Model Context Protocol servers)

These give Claude superpowers. Run each command in your terminal:

**Context7** - Gives Claude access to up-to-date documentation:
```bash
claude mcp add context7 -- npx -y @upstash/context7-mcp@latest
```

**Supabase MCP** - Lets Claude manage your database directly:
```bash
claude mcp add supabase -- npx -y @supabase/mcp-server-supabase@latest \
  --access-token YOUR_SUPABASE_ACCESS_TOKEN \
  --project-ref YOUR_PROJECT_REF
```
> Get your access token from Supabase Dashboard > Settings > API. Get your project ref from the URL: `https://supabase.com/dashboard/project/YOUR_PROJECT_REF`

**Playwright** - Lets Claude take screenshots to verify the UI:
```bash
claude mcp add playwright -- npx -y @anthropic-ai/mcp-server-playwright
```

### Step 5: Install Skills

```bash
claude install-skill anthropics/frontend-design
claude install-skill vercel-labs/find-skills
claude install-skill vercel-labs/vercel-react-best-practices
```

> **Note:** If the command above doesn't work, try `claude plugin install` instead - the exact command may vary by Claude Code version.

See [docs/skills-guide.md](docs/skills-guide.md) for the full analysis of which skills to install and which to skip.

### Step 6: Create Your Project

```bash
mkdir trip-planner && cd trip-planner
```

Copy the `CLAUDE.md` file from this repo into your project folder. This is the single most important file - it tells Claude exactly what to build and how.

Copy `.env.example` to `.env.local` and fill in your API keys.

---

## Phase 1-8: Build the App

Now open Claude Code in your project folder:

```bash
claude
```

Follow the prompts in the `prompts/` folder, **in order**:

| Phase | File | Time | What Happens |
|-------|------|------|-------------|
| 1 | [01-plan.md](prompts/01-plan.md) | 10 min | Plan the architecture (use Plan Mode!) |
| 2 | [02-database.md](prompts/02-database.md) | 5 min | Create database tables via Supabase MCP |
| 3 | [03-scaffold-ui.md](prompts/03-scaffold-ui.md) | 20 min | Scaffold Next.js + build the UI |
| 4 | [04-trip-generation.md](prompts/04-trip-generation.md) | 15 min | Add AI trip generation (Groq) |
| 5 | [05-flight-search.md](prompts/05-flight-search.md) | 15 min | Add real flight search (Kiwi API) |
| 6 | [06-auth-save.md](prompts/06-auth-save.md) | 10 min | Add login + save trips |
| 7 | [07-polish-deploy.md](prompts/07-polish-deploy.md) | 15 min | Polish + deploy to Vercel |
| 8 | [08-visual-check.md](prompts/08-visual-check.md) | 5 min | Verify everything with screenshots |

**Important:** Start Phase 1 in **Plan Mode** (press `Shift+Tab`). Plan Mode is nearly free - it only reads and thinks. Building is expensive. One minute of planning saves ten minutes of building.

---

## Cost Breakdown

| Item | Cost |
|------|------|
| Claude Pro (1 month) | $20 |
| Groq API (app runtime) | $0 |
| Supabase (database + auth) | $0 |
| Vercel (hosting) | $0 |
| Kiwi.com (flight search) | $0 |
| Leaflet (maps) | $0 |
| Domain (optional .xyz) | $0-1 |
| **Total** | **$20** |

The trick: Use **Groq** (free Llama 3.3 70B) for the app's AI feature instead of Claude API. Same quality, zero cost. Claude Pro handles the building.

---

## What You'll Have When Done

- Landing page with trip input form
- AI-generated daily itinerary (food, attractions, tips per day)
- Real flight search with flexible date pricing
- Interactive map with attraction markers
- User login (Google + email)
- Save trips to your account
- Share trips via public URL
- Hebrew RTL interface
- Mobile responsive
- Live on Vercel

---

## Tech Stack

| Layer | Tool | Why This One |
|-------|------|-------------|
| Framework | Next.js 15 (App Router) | Claude knows it best, Vercel deploys it free |
| Styling | Tailwind CSS + shadcn/ui | Claude generates perfect shadcn components |
| Database | Supabase | MCP support = Claude handles it directly |
| AI | Groq (Llama 3.3 70B) | Free, fast, OpenAI-compatible format |
| Flights | Kiwi.com Tequila API | Simple API, good free tier |
| Maps | Leaflet + OpenStreetMap | No API key needed, free forever |
| Hosting | Vercel | Free tier, one-command deploy |

---

## Learn More

- [Credit-Saving Tips](docs/credit-tips.md) - 7 rules to minimize wasted tokens
- [Skills Guide](docs/skills-guide.md) - Deep analysis of every skill and MCP
- [Next Steps](docs/next-steps.md) - RALPH, debugging, and leveling up

---

## Credits

Built by [@peleg.auto](https://instagram.com/peleg.auto)

Guide researched with Claude Code. All tools and APIs listed are free or have free tiers as of March 2026.
