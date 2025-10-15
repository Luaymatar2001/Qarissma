# Qarissma AI Coding Agent Instructions

## Project Overview
- **Framework:** Vue 3 (Single Page Application)
- **Bundler:** Vite
- **Router:** Vue Router
- **Testing:** Vitest + @vue/test-utils (unit tests)
- **Directory Aliases:** `@/` → `src/` (see `vite.config.js` and `jsconfig.json`)

## Key Files & Structure
- `src/` — Main source code
  - `App.vue` — Root component
  - `main.js` — App entry point, sets up Vue and router
  - `router/index.js` — Route definitions (uses code-splitting for `/about`)
  - `components/` — Reusable Vue components
    - `__tests__/` — Unit tests for components (Vitest)
    - `icons/` — SVG icon components
  - `views/` — Page-level components (routed)
  - `assets/` — CSS and static assets
- `vite.config.js` — Vite config, sets up plugins and path aliases
- `vitest.config.js` — Vitest config, merges with Vite config
- `package.json` — Scripts, dependencies, engines
- `README.md` — Setup, build, and test instructions

## Developer Workflows
- **Install dependencies:** `npm install`
- **Start dev server (hot reload):** `npm run dev`
- **Build for production:** `npm run build`
- **Run unit tests:** `npm run test:unit`
- **Preview production build:** `npm run preview`

## Patterns & Conventions
- **Component Style:**
  - Use `<script setup>` in Vue SFCs
  - Scoped styles preferred for components
  - Icons are imported as components from `components/icons/`
- **Routing:**
  - Use `RouterLink` and `RouterView` for navigation
  - Lazy-load route components for code-splitting (see `/about` route)
- **Testing:**
  - Place unit tests in `src/components/__tests__/`
  - Use `@vue/test-utils` and `vitest` for component tests
- **Path Aliases:**
  - Use `@/` for imports from `src/` (e.g., `@/components/HelloWorld.vue`)
- **IDE/Tooling:**
  - Recommended: VS Code + Volar extension (`.vscode/extensions.json`)
  - Use Vue Devtools for debugging

## Integration & External Dependencies
- **Vite Plugins:**
  - `@vitejs/plugin-vue` for Vue SFC support
  - `vite-plugin-vue-devtools` for enhanced debugging
- **No backend/API integration present** (SPA only)
- **No state management (e.g., Pinia) included by default**

## Examples
- **Add a new page:**
  1. Create a new `.vue` file in `src/views/`
  2. Add a route in `src/router/index.js`
- **Add a new component:**
  1. Create a `.vue` file in `src/components/`
  2. Import and use in a parent component
- **Write a unit test:**
  1. Create a `.spec.js` file in `src/components/__tests__/`
  2. Use `@vue/test-utils` and `vitest` APIs

## References
- See `README.md` for setup and workflow details
- See `vite.config.js` and `vitest.config.js` for build/test config
- See `src/components/TheWelcome.vue` for idiomatic component usage

---
For any unclear or missing conventions, please request clarification or examples from project maintainers.
