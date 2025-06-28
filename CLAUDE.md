# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is Anthony Fu's personal talks repository containing presentation slides built with Slidev. It's organized as a pnpm monorepo with date-based presentation folders (e.g., `2025-06-29/`, `2024-12-16/`).

## Common Commands

### Development
- `pnpm dev` - Interactive picker to select and develop a specific presentation (opens in Cursor)
- `pnpm dev -y` - Auto-select the latest presentation for development
- `pnpm run dev` (within presentation src/) - Start Slidev dev server
- `pnpm run build` (within presentation src/) - Build presentation for production
- `pnpm run export` (within presentation src/) - Export presentation as PDF

### Code Quality
- `pnpm lint` - Run ESLint across all presentations
- `pnpm typecheck` - Run Vue TypeScript checking
- `pnpm run build` (root) - Build all presentations

### Maintenance
- `pnpm update` - Update redirects script
- `pnpm prepare` - Initialize git submodules

## Architecture

### Repository Structure
- **Monorepo**: Uses pnpm workspaces (`pnpm-workspace.yaml` points to `*/src`)
- **Date-based folders**: Each presentation in `YYYY-MM-DD/` format
- **Standardized structure**: Each presentation has `src/` with slides, components, and assets

### Key Technologies
- **Slidev**: Vue-based presentation framework
- **Vue 3 + TypeScript**: Frontend stack
- **UnoCSS**: Atomic CSS framework
- **Vite**: Build tool and dev server
- **pnpm**: Package manager with workspace support

### Presentation Structure
Each presentation (`YYYY-MM-DD/src/`) contains:
- `slides.md` - Main slide content in markdown
- `package.json` - Presentation-specific scripts and build config
- `components/` - Custom Vue components (Timeline, Repo, ProsCons, etc.)
- `public/` - Static assets (images, videos, SVGs)
- `vite.config.ts` - Slidev and build configuration
- `style.css` - Custom styling
- `unocss.config.ts` - UnoCSS configuration

### Picker Script
The `scripts/picker.ts` provides:
- Interactive selection of date-based presentations
- Auto-opens selected presentation in Cursor when using `dev` command
- Filters folders matching `^\d{4}-` pattern
- Sorts presentations by date (newest first)

### Build Configuration
- Custom build paths: `--base /YYYY/topic/ --out ../../dist/YYYY/topic`
- PDF export: `--per-slide --output ../YYYY-MM-DD-topic.pdf`
- Magic link markdown extension for automatic linking

### Components Library
Reusable Vue components for presentations:
- `Timeline.vue` - Event timeline visualization
- `Repo.vue` - Repository information display
- `ProsCons.vue` - Pros/cons comparison
- `SetupGraph.vue` - Network/graph visualizations
- `TimeAgo.vue` - Relative time display

## Slidev Presentation Notes
- Focus on leveraging Slidev's native features for transitions
- Ensure comprehensive content presentation without overcrowding slides
- Use multiple transitions to showcase detailed information
- Avoid excessive custom styling
- Maintain clean layout while presenting extensive content

## Development Workflow
1. Run `pnpm dev` to select presentation
2. Modify `slides.md` for content changes
3. Add custom components in `components/` if needed
4. Place assets in `public/` directory
5. Use `pnpm run export` to generate PDF when ready
6. Build all presentations with root `pnpm run build`