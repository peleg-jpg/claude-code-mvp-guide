# Supabase MCP Setup Guide

Official docs: [supabase.com/docs/guides/getting-started/mcp](https://supabase.com/docs/guides/getting-started/mcp)

This page walks you through connecting Claude Code to your Supabase project so Claude can create tables, run queries, and manage your database directly.

---

## Step 1: Create a Supabase Project

1. Go to [supabase.com](https://supabase.com) and sign up (free)
2. Click "New Project"
3. Choose a name, set a database password, pick a region
4. Wait for the project to be created (~30 seconds)

## Step 2: Find Your Project Reference

Your project ref is in the Supabase Dashboard URL:

```
https://supabase.com/dashboard/project/abcdefghijklmnop
                                        ^^^^^^^^^^^^^^^^
                                        This is your project ref
```

Copy this value - you'll need it for the MCP install command.

## Step 3: Install the Supabase MCP

Run this in your terminal:

```bash
claude mcp add supabase -- npx -y @supabase/mcp-server-supabase@latest \
  --project-ref YOUR_PROJECT_REF
```

Replace `YOUR_PROJECT_REF` with the value from Step 2.

### First run: OAuth login

The first time you use the Supabase MCP, it will open your browser for OAuth login. Log in with the same account you used to create the project. No access token needed.

### Alternative: Manual access token (for CI/SSH)

If you can't open a browser (SSH, CI environments):

1. Go to Supabase Dashboard > Account (top right) > Access Tokens
2. Generate a new personal access token
3. Add it to the install command:

```bash
claude mcp add supabase -- npx -y @supabase/mcp-server-supabase@latest \
  --project-ref YOUR_PROJECT_REF \
  --access-token YOUR_ACCESS_TOKEN
```

## Step 4: Get Your Supabase Keys for .env.local

You also need these keys for your app code (not the MCP - the MCP handles its own auth):

1. Go to Supabase Dashboard > Settings > API
2. Copy these two values into your `.env.local`:

```
NEXT_PUBLIC_SUPABASE_URL=https://YOUR_PROJECT_REF.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUz...  (the long JWT)
```

---

## Safety Tips

- **Use a development project.** Don't connect the MCP to your production database. Create a separate Supabase project for development.
- **Read-only mode:** Add `--read-only` to the install command if you want Claude to only read data, not modify it. For this guide, you need write access (Claude creates tables in Phase 2).
- **Project scoping:** The `--project-ref` flag restricts Claude to only this project. It can't access your other Supabase projects.

---

## What Claude Can Do With Supabase MCP

Once connected, Claude can:
- Create and modify database tables
- Write and run SQL queries
- Set up Row Level Security (RLS) policies
- Generate TypeScript types from your schema
- View logs and debug issues
- Manage storage buckets

This is why Phase 2 (Database Setup) takes only 5 minutes - Claude handles the SQL directly.

---

## Troubleshooting

**"MCP not found" error:** Make sure you ran the `claude mcp add` command (Step 3) and restarted Claude Code.

**OAuth window doesn't open:** Use the manual access token method (Step 3 alternative).

**"Permission denied" error:** Make sure you're logged into the same Supabase account that owns the project.

**Tables not appearing in dashboard:** Refresh the Supabase Dashboard. Sometimes there's a 5-10 second delay.
