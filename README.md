# aire-website

Source for [aire.fyi](https://aire.fyi) — the AIRE protocol website.

## Stack

Plain static HTML + CSS. No framework, no build step, no JavaScript dependencies. Deployed via GitHub Pages from `main`.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy

GitHub Pages serves `main` automatically once Pages is enabled in repo settings. The `CNAME` file pins the apex domain (`aire.fyi`).

### One-time go-live checklist

1. Register `aire.fyi` at a registrar (Porkbun, Cloudflare, Namecheap).
2. Configure DNS at the registrar:
   - Apex `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Apex `AAAA` records → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
3. In repo Settings → Pages → enable, source `main` branch, root.
4. In repo Settings → Pages → custom domain → `aire.fyi`, wait for DNS check, enable HTTPS.
5. Flip repo to public.

## License

Apache 2.0 — same as the rest of AIRE.
