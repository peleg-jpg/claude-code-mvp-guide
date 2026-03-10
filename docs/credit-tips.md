# 8 Rules to Minimize Wasted Credits

These tips will save you $10-20 per project. Follow them religiously.

---

## 1. CLAUDE.md is King

Write your CLAUDE.md **BEFORE** your first prompt. This file is loaded into every single message. A good CLAUDE.md means Claude understands your project instantly. A bad one (or none) means Claude guesses - and wrong guesses cost you retries.

**Saves: ~$3-5 per project**

## 2. Plan Mode Before Build Mode

Press `Shift+Tab` to enter Plan Mode. In Plan Mode, Claude only reads and thinks - it doesn't write code. This is nearly free compared to building.

Think of it like this:
- Plan Mode = sketching on paper (cheap)
- Build Mode = pouring concrete (expensive)

Always plan first. One minute of planning saves ten minutes of building.

**Saves: ~$3-5 per project**

## 3. One Big Prompt > Many Small Ones

Every message you send includes the ENTIRE conversation history. So 10 small messages cost way more than 2 big ones that cover the same ground.

Bad (expensive):
```
"Add a button"
"Make it blue"
"Move it to the right"
"Add an icon"
"Make it bigger"
```

Good (cheap):
```
"Add a large blue button with an icon, positioned on the right side"
```

**Saves: ~$2-4 per session**

## 4. Always Say "use context7"

Add "use context7" to every prompt that involves a library or framework. This makes Claude fetch the actual, current documentation instead of guessing from training data.

Without Context7: Claude might hallucinate an API that doesn't exist -> your code breaks -> you retry -> you pay again.

With Context7: Claude reads the real docs -> code works first time.

**Saves: ~$2-5 per project (fewer retry cycles)**

## 5. Don't Install Unnecessary MCPs

Each MCP adds 500-2000 tokens to EVERY prompt. If you have 5 MCPs installed but only use 2, you're paying for 3 MCPs doing nothing.

Only install what you'll actually use for THIS project.

**Saves: ~$1-3 per session**

## 6. Verify with Screenshots, Not Words

Instead of telling Claude "the button is in the wrong place, move it left," use the Playwright MCP to take a screenshot. Claude sees the actual problem and fixes it in one shot.

Describing visual issues in words -> misunderstanding -> wrong fix -> retry.
Screenshot -> Claude sees it -> correct fix -> done.

**Saves: ~$1-3 per visual fix**

## 7. Use /compact When Context Gets Long

After a long conversation, run `/compact` to compress the history. This reduces token count for all future messages in that session.

Do this whenever the conversation starts feeling slow or you've done 10+ back-and-forth messages.

**Saves: ~$1-2 per long session**

## 8. Opus for Planning, Sonnet for Building

Claude Code lets you switch models with `/model`. Use this to your advantage:

- **Phase 1 (planning):** Type `/model opus` - Opus 4.6 is smarter and catches architecture mistakes. Planning uses fewer tokens, so the higher cost per token barely matters.
- **Phases 2-8 (building):** Type `/model sonnet` - Sonnet 4.6 writes code just as well for most tasks, but costs significantly less per token. You get more output per dollar.

Think of it like hiring an architect (Opus) to design the house, then a contractor (Sonnet) to build it. The architect's hourly rate is higher, but you only need them for 10 minutes.

**Saves: ~$3-5 per project**

---

## Total Potential Savings: $16-32 per project

That's the difference between burning through your credits in 1 hour vs. getting a full deployed app.
