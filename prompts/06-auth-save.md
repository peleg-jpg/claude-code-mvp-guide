# Phase 6: Authentication + Save Trips

**Mode: Normal**

**Time: ~10 minutes**

---

## Prompt

```
use context7 for Supabase auth and Next.js docs.

Add authentication and trip saving:

1. Install Supabase auth helpers: npm install @supabase/ssr
2. Set up Supabase auth middleware for Next.js App Router
3. Add auth providers:
   - Email/Password signup and login
   - Google OAuth (configure in Supabase Dashboard > Authentication > Providers)
4. Create a login/signup modal using shadcn Dialog + Tabs (Login | Sign Up)
5. Add a "Save Trip" button on the trip results page:
   - If not logged in: show login modal first
   - If logged in: save trip + itinerary to Supabase
   - Show success toast notification
6. Create /app/my-trips/page.tsx:
   - List all saved trips for the logged user
   - Show destination, dates, budget for each
   - Click to view full trip details
7. Add "Share" button that copies the public URL /trip/[id]
   - Make trips viewable without auth via the is_public flag
8. Update the navbar: show user avatar when logged in, login button when not
```

---

## What to expect

You should be able to sign up, log in, save a trip, and see it in /my-trips. The share URL should work even when logged out.

For Google OAuth: you'll need to configure it in Supabase Dashboard > Authentication > Providers > Google. You'll need a Google Cloud OAuth client ID.
