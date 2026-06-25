# Rivals Rush ⚔️

A browser-based pixel-art action game with 10 difficulty levels, 4 unique bosses, upgrades, a shop, and an online leaderboard.

## Setup

### 1. Supabase Leaderboard
1. Create a free project at [supabase.com](https://supabase.com)
2. Run this SQL in the SQL Editor:
```sql
create table leaderboard (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  score integer not null,
  level integer not null,
  wave integer not null,
  mode text not null,
  created_at timestamp default now()
);
alter table leaderboard enable row level security;
create policy "Anyone can read" on leaderboard for select using (true);
create policy "Anyone can insert" on leaderboard for insert with check (true);
```
3. Go to **Project Settings → API** and copy your Project URL and anon key
4. Open `game.html` and replace:
   - `YOUR_SUPABASE_URL` → your Project URL
   - `YOUR_SUPABASE_ANON_KEY` → your anon key

### 2. Deploy to GitHub Pages
1. Create a new GitHub repo
2. Upload all files in this folder
3. Go to **Settings → Pages → Source: main branch / root**
4. Your site will be live at `https://yourusername.github.io/your-repo-name`

## Files
- `index.html` — Landing page
- `game.html` — Game + leaderboard
- `how-to-play.html` — How to play guide
- `README.md` — This file
