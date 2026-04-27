# CLAUDE.md

Guidance for Claude Code (and other agents) working in the AIRE website repo.

## What this is

Source for [aire.fyi](https://aire.fyi) — the AIRE protocol's manifesto and entry point. Deployed via GitHub Pages on push to `main`.

## Working principles

- **Plain HTML + CSS only.** No JavaScript framework. No build step. No npm. The only file types in this repo should be `.html`, `.css`, `.svg`, plus `CNAME` and `.gitignore`.
- **No telemetry, no analytics, no third-party scripts.** Protocol sites don't track visitors. Models: htmx.org, sqlite.org, redbean.dev.
- **Typography-first.** Dense, opinionated, fast. Should feel like a spec's TL;DR, not a SaaS landing page.
- **Single page.** All sections live in `index.html`. If a second page is genuinely needed, it's a sibling `.html` file using the same `style.css`.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy

GitHub Pages serves `main` automatically. The `CNAME` file pins the apex domain (`aire.fyi`).

DNS lives at Cloudflare:
- Apex `A` records → GitHub Pages IPs (`185.199.108.153`, `…109.153`, `…110.153`, `…111.153`)
- Apex `AAAA` records → `2606:50c0:8000::153` … `…8003::153`
- `www` `CNAME` → `aire-protocol.github.io.`
- **All records gray cloud (DNS only).** Cloudflare proxy breaks GitHub's Let's Encrypt cert provisioning.

HTTPS is enforced; cert is Let's Encrypt via GitHub Pages, auto-renewing.

## Source-of-truth alignment

Manifesto copy lives in two places: this site and `github.com/aire-protocol/aire-spec`'s README. The website may rephrase for browser audience but **must not contradict the spec README**. If you change the bet or comparison table here, update the spec README in the same change set.

## What NOT to add

- ❌ JavaScript bundlers (webpack, Vite, esbuild)
- ❌ Frameworks (React, Vue, Svelte, Astro, Next.js)
- ❌ CSS preprocessors (write plain CSS)
- ❌ Tailwind / utility-class systems
- ❌ Tracking pixels, ad scripts, third-party widgets
- ❌ "Coming soon" banners that get removed later — never commit dev-only scaffolding
- ❌ Service workers, PWA manifests, install prompts
