# AGENTS.md

Instructions for AI coding agents working in this repo.

## Project

React web app that shows Pokemon from PokeAPI (https://pokeapi.co/). Read `plan.md` first for scope and phases. Do not add features outside the plan without asking.

## Stack

- Vite + React 19 (JavaScript, not TypeScript)
- Tailwind CSS + shadcn/ui
- TanStack Query for data fetching
- vite-plugin-pwa for the PWA manifest and icons
- Deploy target: Vercel

## Commands

- Install: `npm install`
- Dev server: `npm run dev`
- Build: `npm run build`
- Preview build: `npm run preview`

## Structure

```
src/
├── components/    # PokemonCard, PokemonList, SearchBar, DetailModal
├── components/ui/ # shadcn/ui generated components (do not hand-edit)
├── hooks/         # usePokemon.js
├── lib/           # utils, API base URL
├── App.jsx
└── main.jsx
```

## Conventions

- One component per file, named export matching the filename.
- All PokeAPI calls go through `src/hooks/usePokemon.js`. Components never call `fetch` directly.
- Use TanStack Query for every request. No `useEffect` + `fetch`.
- Pagination: 20 per page, using `offset` and `limit` on `/pokemon`.
- Search: exact name lookup on `/pokemon/{name}`, lowercased before the request.
- Detail view shows the first 10 moves only.
- Add UI with shadcn components (`npx shadcn@latest add <name>`) before writing custom ones.
- Use Tailwind classes. No inline style objects unless needed for a computed value.

## Rules

- Never commit secrets or `.env` files. PokeAPI needs no key.
- Keep PokeAPI as the only data source. Do not add a backend.
- Do not change `plan.md` decisions without the user's approval. Note any change you think is needed and ask.
- Run `npm run build` before saying a task is done. Fix any errors it reports.
- Keep commits small, one phase or feature per commit, with clear messages.

## Done check

A task is done when it works in `npm run dev`, `npm run build` passes, and it matches the phase in `plan.md`.
