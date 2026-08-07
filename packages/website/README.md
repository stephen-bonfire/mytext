# MyText Website

The marketing site and documentation for [MyText](https://github.com/stephen-bonfire/mytext).

This is a package inside the MyText monorepo, not a standalone repository. Clone the
monorepo and work from its root; see the repository's `CONTRIBUTING.md`.

## Stack

- **Next.js 15** (App Router) + **React 19** + **TypeScript**
- **Tailwind CSS 4**
- Deployed to **Cloudflare Workers** via [OpenNext](https://opennext.js.org/cloudflare)

Docs pages are generated from Markdown under `content/`. `scripts/build-docs-index.ts`
builds the search index and runs automatically before `dev` and `build`.

## Commands

Run from the monorepo root:

```bash
pnpm --filter mytext-website dev          # dev server on :3000
pnpm --filter mytext-website build        # production build
pnpm --filter mytext-website start        # serve the production build
pnpm --filter mytext-website type-check   # tsc --noEmit
pnpm --filter mytext-website lint         # eslint, zero-warning policy
pnpm --filter mytext-website docs:index   # rebuild the docs search index only
```

Cloudflare-specific:

```bash
pnpm --filter mytext-website cf:build     # OpenNext build + local cache populate
pnpm --filter mytext-website cf:preview   # preview the Worker locally
```

## Deployment

`.github/workflows/website-deploy.yml` handles this — there is no manual deploy step.
A push to `main` that touches `packages/website/**` deploys to production; a pull
request uploads a preview version and comments the URL on the PR.

The Worker is named `marktext-website` (`wrangler.toml`). That name is intentionally
unchanged by the MyText rename: renaming it would provision a *new* Worker and orphan
the existing deployment and its DNS.

## Layout

```
packages/website/
├── content/              Markdown source for the docs section
├── public/               Static assets
├── scripts/              build-docs-index.ts
├── src/                  App Router routes, components, lib
├── next.config.ts
├── open-next.config.ts   OpenNext → Cloudflare adapter config
└── wrangler.toml         Cloudflare Worker config
```
