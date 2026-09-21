# Azure Terraform Backend Bootstrap

Reveal.js talk deck on the Day 0 problem of provisioning a secure Azure remote backend for Terraform — options considered, why Bicep, and how the blueprint works.

**Live deck (after Pages is enabled):** [https://jrabbott.github.io/talk-azure-terraform-backend/](https://jrabbott.github.io/talk-azure-terraform-backend/)

## Sources

- [blueprint-azure-terraform-backend](https://github.com/jrabbott/blueprint-azure-terraform-backend)
- [ADR: Bootstrap Terraform state storage](https://dfe-digital.github.io/accessing-childcare-entitlement-checker/reference/decisions/bootstrap-tf/)
- [How-to: Terraform state bootstrapping](https://dfe-digital.github.io/accessing-childcare-entitlement-checker/how-to/terraform-bootstrap/)

## Requirements

- **Node.js 22+** (see `.nvmrc`). Prefer `npm ci` so the lockfile is respected.

## Run locally

```bash
npm ci
npm run dev
```

Open the URL Vite prints (usually `http://localhost:5173/talk-azure-terraform-backend/`).

To check the production build:

```bash
npm run build
npm run preview
```

Dependency audit (also runs in CI):

```bash
npm run audit
```

## Present

1. Start with `npm run dev` (or open the live Pages URL).
2. Click the slides, then use arrow keys / space to navigate.
3. Press `F` for fullscreen, `S` for speaker notes, `Esc` for overview.
4. Slide numbers and URL hashes are enabled so you can deep-link to a slide.
5. Fragments advance with the same keys; code blocks can step line ranges via `data-line-numbers`.

## Deck outline (12 slides)

1. Title — Bootstrapping Azure Terraform state
2. The problem — chicken-and-egg Day 0
3. Challenges & requirements
4. Options — Portal, CLI, ARM, Bicep
5. Decision — bootstrap with Bicep
6. Advantages of the chosen approach
7. Architecture diagram
8. What Bicep provisions
9. Hardened-by-default security
10. Pipeline access to private state storage
11. Implementation — deploy + Terraform backend
12. Closing / references

## Theming

Brand tokens live at the top of `src/style.css` (`--ink`, `--accent`, etc.). Fonts are DM Sans via `@fontsource/dm-sans` in `src/main.js`.

## CI and publish

Shared quality gate lives in `.github/actions/build` (`npm ci`, audit, Vite build with repo-derived `BASE_PATH`, `dist/` smoke check).

- **CI** (`.github/workflows/ci.yml`) runs that action on pull requests.
- **CD** (`.github/workflows/cd.yml`) runs the same action on pushes to `main` (or `workflow_dispatch`), uploads `dist/`, and deploys to GitHub Pages.
