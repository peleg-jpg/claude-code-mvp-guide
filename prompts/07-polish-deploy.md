# Phase 7: Polish + Deploy

**Mode: Normal**

**Time: ~15 minutes**

---

## Prompt

```
Final polish and deployment:

1. Add loading states:
   - Skeleton screens while trip generates
   - Spinner on flight search
   - Loading state on all buttons

2. Add error handling:
   - Show user-friendly error if OpenRouter API fails
   - Show fallback if flight search returns no results
   - Handle network errors gracefully

3. Add meta tags for sharing:
   - Dynamic OG title: "Trip to [destination] - [days] days"
   - OG description with budget info
   - Add a default OG image

4. Responsive design check:
   - Make sure the form works on mobile
   - Stack cards vertically on small screens
   - Hide map on very small screens, show button to expand

5. Run the build and fix any errors:
   - npm run build
   - Fix all TypeScript errors
   - Fix any hydration mismatches

6. Deploy to Vercel:
   - git init
   - git add -A
   - git commit -m "Trip planner MVP"
   - Push to GitHub (create a new repo)
   - Connect to Vercel: vercel deploy
   - Add all env vars in Vercel Dashboard > Settings > Environment Variables
```

---

## What to expect

After deployment, you'll have a live URL like `trip-planner-abc.vercel.app`. Test it on your phone to make sure mobile works.

If the build fails, paste the error into Claude and it will fix it.
