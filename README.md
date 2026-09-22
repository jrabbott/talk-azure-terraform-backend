# Bootstrapping Azure Terraform state

Reveal.js talk deck on the Day 0 problem of provisioning a secure Azure remote backend for Terraform — options considered, why Bicep, and how the blueprint works.

## Requirements & run locally

- **Node.js 22+** (see `.nvmrc`). Prefer `npm ci` so the lockfile is respected.

```bash
npm ci
npm run dev
```

Open the URL Vite prints (usually `http://localhost:5173/talk-azure-terraform-backend/`).

## Present

1. Start with `npm run dev`.
2. Click the slides, then use arrow keys / space to navigate.
3. Press `F` for fullscreen, `S` for speaker notes, `Esc` for overview.
4. Slide numbers and URL hashes are enabled so you can deep-link to a slide.
5. Fragments advance with the same keys; code blocks can step line ranges via `data-line-numbers`.

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

## License

MIT — see [LICENSE](./LICENSE).
