# 🖖 Star Trek Explorer — Live Coding Task

You have **30 minutes**. You do not need to finish.
Use any tools at your disposal — AI assistants, docs, Google, anything.

---

## Goal

Build a React app called **Star Trek Explorer** using the STAPI public API:
Base URL: https://stapi.co/api/v1/rest

A Figma design is provided and should be used as the visual reference.

---

## API Overview

STAPI requires no API key.
Search endpoints use POST with application/x-www-form-urlencoded.

Endpoint              | Method | Key Params
/character/search     | POST   | name, gender, deceased, pageNumber, pageSize
/character/{uid}      | GET    | uid
/species/search       | POST   | name, pageNumber

Example request:

POST https://stapi.co/api/v1/rest/character/search
Content-Type: application/x-www-form-urlencoded
name=Spock&pageSize=10&pageNumber=0

---

## Requirements

Work through these in order — earlier items are higher priority.

### 1. Search Bar
- Debounced input with a 300ms delay.
- Calls /character/search as the user types.
- Should not fire on every keystroke.

### 2. Character Card Grid
- Responsive grid layout.
- Each card shows: name, gender, species.
- Avatar is initials-based, no images required.
- Avatar color can vary by gender or another simple rule.

### 3. Filter Sidebar
- Gender: M / F / Unknown.
- Deceased: boolean toggle.
- Mirror Universe: boolean toggle.
- Filters should trigger a new API fetch, not pure client-side filtering.
- Note: STAPI only accepts M and F as API values. Unknown means gender is null — handle it client-side.

### 4. Pagination
- "Load more" button or page controls.
- Use pageNumber and pageSize params.

### 5. Character Detail Drawer
- Clicking a card opens a right-side drawer.
- Fetch full character data from GET /character/{uid}.
- Show: name, gender, species, year of birth/death, mirror universe flag.

### 6. Favorites
- Heart icon on each card.
- Favorited characters persist in localStorage.
- UI updates optimistically on click.

### 7. Comparison Mode (stretch)
- Select exactly 2 favorited characters.
- Render a side-by-side attribute table.
- Matching values stay neutral.
- Differing values highlighted: red on left, green on right.

### 8. URL Sync (stretch)
- Search term and active filters reflected in URL query params.
- Refreshing or sharing the URL restores the same state.

---

## What We're Looking For

Area               | What to observe
Prioritization     | Do they tackle the most important features first?
AI prompting       | Do they break the task into focused prompts?
Debugging          | Do they inspect API responses and catch nested-data issues?
State architecture | Is shared state handled cleanly across drawer, favorites, comparison?
Code review        | Do they validate AI-generated code before using it?

---

## Suggested Stack

You may use any stack. Suggested default:
- Vite + React + TypeScript
- Tailwind CSS
- @tanstack/react-query

---

## Notes

The task is intentionally larger than 30 minutes. You are not expected to finish.
We care about how you prioritize, how you use AI, how you debug, and how you explain tradeoffs.
