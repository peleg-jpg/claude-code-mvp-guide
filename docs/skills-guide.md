# Skills & MCPs Guide: What to Install, What to Skip

Every skill and MCP adds tokens to your context window. The right ones save you money. The wrong ones burn it.

---

## MCPs (Model Context Protocol Servers)

MCPs give Claude access to external tools and services.

### Install These (3 total)

| MCP | What It Does | Why It Saves Credits | Install |
|-----|-------------|---------------------|---------|
| **Context7** | Fetches up-to-date docs for any library | Prevents hallucinated APIs that cause retry loops | `claude mcp add context7 -- npx -y @upstash/context7-mcp@latest` |
| **Supabase** | Lets Claude manage your database directly | No need to explain SQL - Claude just does it | `claude mcp add supabase -- npx -y @supabase/mcp-server-supabase@latest --access-token TOKEN --project-ref REF` |
| **Playwright** | Claude takes screenshots of your app | Catches visual bugs before you even look | `claude mcp add playwright -- npx -y @anthropic-ai/mcp-server-playwright` |

### Skip These

| MCP | Why Skip |
|-----|----------|
| **Obsidian** | Knowledge management - not for building apps |
| **Vercel MCP** | Not mature. `vercel deploy` in terminal is simpler |
| **Firecrawl** | Web scraping - not needed when you have specific APIs |
| **Figma MCP** | Only useful if you have Figma designs to implement |
| **Linear/GitHub Issues** | Project tracking - overkill for a 2-hour sprint |
| **Extra search MCPs** | Apify, SerpAPI, etc. - add context bloat |

---

## Skills

Skills are instruction files that guide Claude's behavior. Each one adds ~500-2000 tokens to every prompt.

### Tier 1: Must Install

**frontend-design** (Anthropic Official - 124K installs)
- Gives Claude a design philosophy: 50 styles, 21 palettes, 50 font pairings
- Makes UI look professional on first render
- Without it: expect 3-4 "make it look better" retries ($3-5 wasted)
- **ROI: 3-5x return on context cost**
- Install: `claude plugin install anthropics/frontend-design`

**find-skills** (Vercel Labs - 418K installs, #1 most installed)
- Meta-skill that discovers and installs other skills
- Near-zero context cost (~200 tokens)
- Useful when you need a skill mid-project but don't know which one
- Install: `claude skill install vercel-labs/find-skills`

### Tier 2: Recommended

**vercel-react-best-practices** (176K installs)
- Codified React/Next.js patterns for production apps
- Prevents common App Router mistakes
- Context cost: ~1000 tokens
- Install: `claude skill install vercel-labs/vercel-react-best-practices`

### Tier 3: Learn for Later (Don't Install for First Project)

**RALPH** (snarktank/ralph - 57K installs)
- An autonomous coding loop that spawns fresh Claude sessions per user story
- How it works:
  1. You write a PRD (Product Requirements Document)
  2. RALPH breaks it into user stories
  3. Spawns a NEW Claude session for each story (clean context!)
  4. Runs quality checks after each
  5. Commits and repeats until done
- Why it's smart: Fresh context per task prevents degradation
- **Why skip for first project:**
  - Writing a PRD takes 15-20 min (10% of your 2-hour window)
  - You don't learn how Claude Code works (RALPH abstracts too much)
  - Needs test infrastructure for the feedback loop
- **Perfect for project #2:** "You built your first app step by step. Now install RALPH and build the next one 5x faster."
- GitHub: https://github.com/snarktank/ralph

**skill-creator** (Anthropic Official)
- Lets you create custom skills that teach Claude specific workflows
- Example: After building 3 apps, you notice you always set up Supabase the same way - create a skill so Claude does it automatically next time
- Why skip for first project: You need to understand Claude's workflow patterns before you can codify them into skills. It's a tool for making tools.
- **Perfect for project #3+:** Once you've spotted your repeated patterns, package them as skills

**systematic-debugging**
- Methodical debugging with hypothesis -> evidence -> root cause
- Useful when something breaks mysteriously
- For most bugs, Playwright screenshots are enough

**brainstorming**
- Structured ideation before coding
- Plan Mode does 80% of this already
- Useful when exploring ideas, not executing a known spec

### Tier 4: Skip for MVP

| Skill | Installs | Why Skip |
|-------|----------|----------|
| web-design-guidelines | 137K | Overlaps with frontend-design |
| test-driven-development | ~50K | TDD adds 40% time - skip for 2-hour MVP |
| code-review | 50K | No time for formal review |
| security-guidance | 25K | Important for prod, not for MVP demo |
| feature-dev | N/A | Multiple sub-agents = burns context |
| GSD workflow | N/A | Designed for multi-week projects |
| All SEO/marketing skills | N/A | Not relevant for MVP building |
| All CRO/conversion skills | N/A | Post-launch optimization |

---

## Summary: The New User MVP Kit

```
INSTALL:
  Skills:  frontend-design + find-skills + vercel-react-best-practices
  MCPs:    Context7 + Supabase MCP + Playwright
  VS Code: rtl-for-vs-code-agents (for Hebrew users)

CONTEXT OVERHEAD: ~3000 tokens per prompt
CREDIT SAVINGS vs VANILLA: $8-15

LEARN FOR PROJECT #2:
  - RALPH (autonomous coding loop)
  - systematic-debugging
  - brainstorming

LEARN FOR PROJECT #3+:
  - skill-creator (create your own custom skills)
```
