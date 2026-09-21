# Azure Terraform Backend Bootstrap

Reveal.js talk deck on the Day 0 problem of provisioning a secure Azure remote backend for Terraform — options considered, why Bicep, and how the blueprint works.

**Live deck (after Pages is enabled):** [https://jrabbott.github.io/talk-azure-terraform-backend/](https://jrabbott.github.io/talk-azure-terraform-backend/)

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

Speaker notes in `<aside class="notes">` are author-controlled HTML rendered by reveal.js in the speaker view. Treat them as trusted content only—do not paste untrusted markup into notes.

## Deck outline

1. Title — Bootstrapping Azure Terraform state
2. Section — The Day 0 problem
3. The problem — chicken-and-egg Day 0
4. Challenges & requirements
5. Section — Choosing an approach
6. Options — Portal and CLI
7. Options — ARM and Bicep
8. Decision — bootstrap with Bicep
9. Advantages of the chosen approach
10. Section — The blueprint
11. Architecture diagram
12. What Bicep provisions
13. Hardened-by-default security
14. Pipeline access to private state storage
15. Deploy the bootstrap — `az deployment sub create`
16. Point Terraform at the backend — `backend "azurerm"`
17. Closing

### Layout classes

| Class | Use in this deck |
| --- | --- |
| `slide-title` | Opening title + speaker |
| `slide-section` / `section-alt` | Full-bleed section breaks |
| `slide-list` | Bullets with fragments |
| `slide-modes` | Two-column comparison |
| `slide-diagram` | Full-bleed architecture diagram |
| `slide-code` | Syntax-highlighted code |
| `slide-closing` | Closing line |

## Theming

Aligned with the [slides-as-code](https://github.com/jrabbott/slides-as-code) template. Brand tokens live at the top of `src/style.css`:

```css
:root {
  --ink: #121820;
  --muted: #2c3544;
  --surface: #f2eee6;
  --accent: #0c6b52;
  --accent-soft: #c5e4d8;
  --on-accent: #f2eee6;
  --closing: #121820;
}
```

Content slides share one solid paper colour (`--surface`). Section and closing slides use solid accent or ink. Defaults lean dyslexia-friendly:

- [Atkinson Hyperlegible](https://brailleinstitute.org/freefont) with open letter/word spacing
- Sentence-case labels; prefer **bold** over italic for emphasis
- Quiet motion (`transition: 'none'`; plain `fragment` without travel)
- Light syntax colours on paper (no dark Monokai block)
- Calmer 1–2 column layouts

Swap fonts via `@fontsource/atkinson-hyperlegible` in `src/main.js` and the `--r-*-font` / spacing variables.

## CI and publish

Shared quality gate lives in `.github/actions/build` (`npm ci`, audit, Vite build with repo-derived `BASE_PATH`, `dist/` smoke check).

- **CI** (`.github/workflows/ci.yml`) runs that action on pull requests.
- **CD** (`.github/workflows/cd.yml`) runs the same action on pushes to `main` (or `workflow_dispatch`), uploads `dist/`, and deploys to GitHub Pages.
