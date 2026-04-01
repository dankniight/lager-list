# Lager List 🍺

A shared lager tracking app for you and your friends. Built with Supabase and hosted on GitHub Pages.

## Features

- ✅ Add lagers with name, location, and ratings
- ✅ Real-time updates - everyone sees changes instantly
- ✅ Edit entries inline
- ✅ Free to host (Supabase free tier + GitHub Pages)
- ✅ No login required

## Setup (5 minutes)

### Step 1: Create Supabase Project

1. Go to [Supabase](https://supabase.com/)
2. Sign in and click **New Project**
3. Enter any project name (e.g., "lager-list")
4. Set a database password (save it somewhere safe)
5. Choose a region close to you
6. Click **Create project** (takes ~2 minutes)

### Step 2: Create the Lagers Table

1. In your Supabase project, go to **Table Editor** (sidebar)
2. Click **New Table**
3. Create a table called `lagers` with these columns:

| Name | Type | Default | Primary |
|------|------|---------|---------|
| `id` | int8 | auto-increment | ✓ |
| `name` | text | | |
| `location` | text | | |
| `bag_rating` | int2 | null | |
| `matt_rating` | int2 | null | |
| `damo_rating` | int2 | null | |
| `dank_rating` | int2 | null | |
| `jamie_rating` | int2 | null | |
| `pin_rating` | int2 | null | |
| `rod_rating` | int2 | null | |
| `tim_rating` | int2 | null | |
| `created_at` | timestamptz | `now()` | |

4. Click **Save**

### Step 3: Enable Row Level Security (RLS)

1. Go to **Authentication → Policies**
2. Find the `lagers` table
3. Click **Enable RLS**
4. Add a new policy:
   - Name: "Allow all operations"
   - Allowed operation: `ALL`
   - Target roles: `postgres` and `anon`
   - Policy definition: `true`
5. Click **Save**

> **Security note:** This allows anyone with your anon key to read/write. For a private list, you can add authentication later.

### Step 4: Get Your Supabase Credentials

1. Go to **Settings → API**
2. Copy these two values:
   - **Project URL** (e.g., `https://xxxxx.supabase.co`)
   - **anon public** key (the long JWT string starting with `eyJ...`)

### Step 5: Add GitHub Secrets

1. Go to your GitHub repository
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **New repository secret** and add:

| Secret Name | Value |
|-------------|-------|
| `SUPABASE_URL` | Your Project URL from step 4 |
| `SUPABASE_ANON_KEY` | Your anon public key from step 4 |

### Step 6: Deploy to GitHub Pages

1. In your GitHub repo, go to **Settings → Pages**
2. Under **Build and deployment**:
   - Source: **Deploy from a branch**
   - Branch: **main** (or master)
   - Folder: **/ (root)**
3. Click **Save**
4. Go to **Actions** tab and enable workflows if prompted
5. Your site will be live at `https://yourusername.github.io/lager-list`

Done! Start adding lagers! 🍺

## Sharing with Friends

Send your friends the GitHub Pages URL. The Supabase config is automatically injected, so they can start rating lagers immediately!

## Supabase Free Tier Limits

- 500 MB database storage
- 50,000 monthly active users
- Unlimited API requests
- 2 GB bandwidth/month

More than enough for tracking lagers! 🍻

## Local Development

To test locally without GitHub Actions:

1. Open `index.html` in a browser
2. Click the setup notice banner
3. Enter your Supabase URL and anon key
4. Config is saved in localStorage

## Data Structure

Data is stored in Supabase PostgreSQL:

```
lagers table:
- id: bigint (auto-increment)
- name: text
- location: text
- bag_rating: int2 (1-10, nullable)
- matt_rating: int2 (1-10, nullable)
- damo_rating: int2 (1-10, nullable)
- dank_rating: int2 (1-10, nullable)
- jamie_rating: int2 (1-10, nullable)
- pin_rating: int2 (1-10, nullable)
- rod_rating: int2 (1-10, nullable)
- tim_rating: int2 (1-10, nullable)
- created_at: timestamptz
```
