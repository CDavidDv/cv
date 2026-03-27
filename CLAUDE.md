# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a CV/portfolio website built with **Astro** and **TypeScript**. It's a data-driven application where CV content is stored in JSON files and rendered by Astro components. The site includes bilingual support (Spanish/English) via separate JSON data files.

## Development Commands

| Command | Purpose |
|---------|---------|
| `npm run dev` | Start local dev server at `http://localhost:4321` |
| `npm run build` | Build production site to `./dist/` |
| `npm run preview` | Preview production build locally |
| `npm run astro` | Run Astro CLI directly (e.g., `npm run astro add`) |

## Project Structure

- **`src/pages/index.astro`** — Main CV page. Composes all section components and imports them into a layout.
- **`src/components/sections/`** — Section components (Hero, About, Experience, Education, Projects, Skills). Each renders data from the JSON CV file.
- **`src/components/`** — Shared components (Section wrapper, KeyboardManager for shortcuts).
- **`src/icons/`** — SVG icon components (skill icons, social links).
- **`src/layouts/Layout.astro`** — Page layout wrapper.
- **`src/cv.json` / `src/cv_english.json`** — Data files containing all CV content (follows JSON Resume schema). These are imported via path alias `@cv`.

## Key Architecture Patterns

**Data-driven design:** All CV content lives in JSON files. Section components import the appropriate CV data file and iterate over arrays (work experience, education, projects, etc.) to render content. This separation makes content updates independent of component changes.

**Path aliases:** TypeScript paths are configured in `tsconfig.json`:
- `@/` → `src/`
- `@cv` → `src/cv.json`

Use these aliases in imports throughout the project.

**Astro components:** All components are `.astro` files. The main page composes section components within a `Layout` component. The `KeyboardManager` component likely handles keyboard shortcuts/interactions.

## Common Tasks

- **Update CV content:** Edit `src/cv.json` (Spanish) or `src/cv_english.json` (English). Section components automatically render updated data on save.
- **Modify a section's styling:** Edit the relevant component in `src/components/sections/` (e.g., `Experience.astro` for work experience styling).
- **Add new icons:** Create a new `.astro` file in `src/icons/` following the existing pattern.
- **Change layout/structure:** Edit `src/layouts/Layout.astro` or modify which sections appear in `src/pages/index.astro`.

## Notes

- The README.md is a generic Astro starter template and is outdated relative to the actual project.
- The project uses minimal dependencies: Astro, ninja-keys (for keyboard shortcuts).
