# Pokemon App: Plan

## Goal

A React web app that lists Pokemon from PokeAPI (https://pokeapi.co/), lets the user search by name, load more, and open a detail view. Installable as a PWA. Deployed on Vercel. Target build time: about 2 days.

## Decisions (defaults chosen, change here if needed)

- Styling: Tailwind CSS + shadcn/ui
- Data: TanStack Query (React Query)
- PWA: installable only (web manifest + icons). No offline caching in this version.
- Hosting: Vercel
- Pagination: 20 Pokemon per "Load more"
- Search: exact name lookup against PokeAPI (`/pokemon/{name}`), case-insensitive, with a clear "not found" message
- Detail view: first 10 moves, scrollable list, abilities, height, weight

## Stack

- Vite + React 19
- Tailwind CSS, shadcn/ui components
- TanStack Query for fetching, caching and pagination
- vite-plugin-pwa for the manifest and icons
- Deployed to Vercel

## Phases

### Phase 1: Setup

- Scaffold Vite React app in the repo root
- Install Tailwind and initialize shadcn/ui
- Add TanStack Query provider in `main.jsx`
- Confirm `npm run dev` works

### Phase 2: Data layer

- `src/hooks/usePokemon.js`: list query (paginated, 20 per page), single-Pokemon query, detail query
- Handle loading and error states in the hook, not in components

### Phase 3: List and cards

- `PokemonCard`: sprite, name, type badges, base stats (HP, Attack, Defense, Speed)
- `PokemonList`: grid of cards, "Load more" button
- Loading skeletons and an error message

### Phase 4: Search

- `SearchBar`: text input, submits on Enter or button
- Empty input resets to the normal list
- Unknown name shows "No Pokemon found"

### Phase 5: Detail view

- `DetailModal`: opens on card click, closes on Escape or outside click
- Shows height, weight, abilities, first 10 moves
- Uses a shadcn Dialog

### Phase 6: PWA

- Web manifest: name, short name, theme color, display `standalone`
- App icons at 192px and 512px
- Confirm install prompt works in Chrome on desktop and Android

### Phase 7: Polish and deploy

- Responsive check on phone width
- README with screenshot, live link, setup steps and tech list
- Connect GitHub repo to Vercel and deploy

## Out of scope (for this version)

- Offline caching of data
- User accounts or favorites
- Full move list (only first 10 are shown)
- Evolution chains

## Done means

- Cards load, load more works, search works, detail modal works
- App installs as a PWA
- Live link on Vercel, README complete
