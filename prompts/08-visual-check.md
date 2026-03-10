# Phase 8: Visual Verification

**Mode: Normal**

**Time: ~5 minutes**

---

## Prompt

```
Use Playwright to visually verify the app. Navigate to localhost:3000 and:

1. Take a screenshot of the main form page
2. Fill in the form with: destination "Tokyo", budget 2000, 5 days, dates next month
3. Submit and take a screenshot of the loading state
4. Take a screenshot of the generated trip results
5. Take a screenshot of the flights section
6. Resize browser to 375px width and take mobile screenshots of the same pages
7. Check for any visual issues: broken layouts, overlapping text, missing elements

Fix any visual problems you find.
```

---

## What to expect

Claude will use the Playwright MCP to control a browser, take screenshots, and show them to you. This is cheaper than going back and forth describing what's wrong - Claude sees the issues directly.

This is your final quality check before sharing the app.

---

## You're done!

Your trip planner is now live. Share the Vercel URL with friends.

Total time: ~2 hours
Total cost: $20 (Claude Pro)
Everything else: free

See [docs/next-steps.md](../docs/next-steps.md) for what to learn next.
