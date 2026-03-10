# Next Steps: After Your First MVP

You just built and deployed a real app in 2 hours. Here's what to learn next.

---

## Level Up: RALPH Autonomous Loop

Now that you understand how Claude Code works, install RALPH for your next project:

```bash
claude plugin install snarktank/ralph
```

RALPH automates the build cycle:
1. Write a PRD (Product Requirements Document) describing your app
2. RALPH breaks it into user stories
3. Spawns fresh Claude sessions for each story
4. Runs quality checks
5. Commits and repeats

For your first RALPH project, try something with clear, small stories - like a todo app with user accounts, or a simple dashboard.

GitHub: https://github.com/snarktank/ralph

---

## Create Your Own Skills with skill-creator

After 2-3 projects, you'll notice patterns you keep repeating. The **skill-creator** (Anthropic Official) lets you package those into reusable instructions that Claude follows automatically.

Example use cases:
- **Project scaffolding** - "Always set up Next.js + Supabase + shadcn/ui this way"
- **API integration patterns** - "When connecting to any OpenAI-compatible API, follow these steps"
- **Your coding standards** - "Use these naming conventions, folder structure, and error handling patterns"

A skill is just a markdown file with structured instructions. skill-creator guides you through writing one that actually works.

---

## More MCPs to Explore

| MCP | What It Does | When to Add |
|-----|-------------|-------------|
| **GitHub MCP** | Claude manages PRs, issues, branches | When working on team projects |
| **Figma MCP** | Claude reads Figma designs and generates code | When you have a designer |
| **Chrome DevTools** | Claude debugs live browser sessions | When debugging complex frontend issues |

---

## More Skills to Try

| Skill | What It Does | When to Add |
|-------|-------------|-------------|
| **systematic-debugging** | Scientific debugging method | When bugs get mysterious |
| **brainstorming** | Structured ideation | When exploring new project ideas |
| **test-driven-development** | TDD workflow | When building production features |
| **code-review** | Multi-agent code review | Before deploying to production |

---

## Improve Your Trip Planner

Ideas for v2 (each could be a 30-min session):

1. **Hotel search** - Add Booking.com or Airbnb API for accommodation
2. **Weather forecast** - Show weather for travel dates using OpenWeather free API
3. **Budget tracking** - Let users log actual expenses during the trip
4. **Multi-language** - Add English/Hebrew toggle
5. **PDF export** - Generate a printable trip plan
6. **Social sharing** - OG images with trip preview for Instagram/WhatsApp

---

## Save Money on Future Projects

- Always start with Plan Mode
- Use the same CLAUDE.md template pattern
- Pick free-tier tools (Groq, Supabase, Vercel, Leaflet)
- Install only the MCPs you need for THIS project
- Read [credit-tips.md](credit-tips.md) before every session
