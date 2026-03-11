# Madness Tracker 🏀

[Deployed Webpage](https://m-duffy.github.io/madness-tracker/)
A lightweight March Madness draft tracker. Players draft teams from the men's and women's NCAA tournaments and earn points based on how far their teams advance. Scores update automatically as results are entered.

## Features

- **Leaderboard** — separate men's, women's, and combined standings with per-player team breakdowns
- **Bracket view** — classic NCAA bracket layout, color-coded by draft owner
- **Rosters** — each player's teams and win counts per tournament
- **Manually updated** — backed by Google Sheets, refresh the page to see latest results

## Stack

- Plain HTML/CSS/JS — single `index.html`, no build step
- Hosted on GitHub Pages (free)
- Google Sheets as the data backend
- Google Forms for entering game results on mobile

## Setup

### 1. Google Sheets
Create a spreadsheet with the following tabs:

| Tab | Columns |
|---|---|
| `players` | `player`, `color` (hex) |
| `draft` | players as column headers (B1:I1), picks in rows 2–9 |
| `bracket_m` | `slot`, `team`, `seed`, `slot` |
| `bracket_w` | `slot`, `team`, `seed`, `slot` |
| `teams_m` | formula-driven — see below |
| `teams_w` | formula-driven — see below |
| `results_m` | formula-driven — see below |
| `results_w` | formula-driven — see below |

Share the sheet as **Anyone with the link can view**.

### 2. Google Forms
Create two forms (one mens, one womens), each with:
- **Round** — multiple choice: `Round of 64`, `Round of 32`, `Sweet 16`, `Elite Eight`, `Final Four`, `Championship`
- **Winning Team** — dropdown of all 64 teams

Set each form to save responses to a sheet tab named `Mens Responses` and `Womens Responses`.

### 3. Google Sheets API Key
- Go to [console.cloud.google.com](https://console.cloud.google.com)
- Create a project → Enable **Google Sheets API**
- Create an API key → Restrict it to HTTP referrer `yourusername.github.io/*`

### 4. GitHub Pages
- Push `index.html` and `README.md` to a public repo
- Go to **Settings → Pages → Source: main branch**
- Open `yourusername.github.io/madness-tracker` and enter your Sheet ID and API key when prompted — these are saved in your browser

## Scoring

| Round | Points |
|---|---|
| Round of 64 | 3 |
| Round of 32 | 4 |
| Sweet 16 | 5 |
| Elite Eight | 6 |
| Final Four | 7 |
| Championship | 8 |

## Draft Rules

Each player drafts 8 teams from the men's bracket. They automatically receive the team in the same slot from the women's bracket.
