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
----------------------|--------|--------------------------------------------------
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

## App State & Data Flow

On initial load, the app fetches all or fixed numbers of characters (empty name param) and displays
them in the grid. This is the default state — no search needed to see content.

Search and filters are always combined into a single API call. There is no
separate filter request. Every change to the search term or any filter (via accept filters button) resets
the page to 0 and fires a new fetch with all active params included.

Example — user has typed "Kirk" and toggled gender to M:

POST /character/search
name=Kirk&gender=M&pageNumber=0&pageSize=10

Clearing the search term does not clear the filters, and vice versa.

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
- Filters are always combined with the current search term in one API call.
- Changing any filter resets pagination to page 0.
- Note: STAPI only accepts M and F as gender API values.
  Unknown (null gender) must be fetched without a gender param and filtered client-side.

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

## Suggested Stack

You may use any stack. Suggested default:
- Vite + React + TypeScript
- Tailwind CSS
- @tanstack/react-query

---

## Notes

The task is intentionally larger than 30 minutes. You are not expected to finish.
We care about how you prioritize, how you use AI, how you debug, and how you explain tradeoffs.
