# tdtm.io

Marketing site for **TDTM — Talk Data To Me**. Static single page, deployed as a
Cloudflare Worker (Static Assets). Every CTA points to the app at
`https://talkdatatome.online`.

Positioning note: this page sells the outcomes and keeps the internals vague on
purpose — no exact field counts, no partner names, no API mechanics, no
self-learning details. Keep it that way.

## Structure

```
index.html        the whole site (inline CSS, no build step)
brand/            TDTM logo + icon variants (from the brand package)
tdtm-og.png       social share image (og:image / twitter:image)
wrangler.jsonc    Cloudflare Worker config
.assetsignore     files excluded from the public deploy
```

## Deploy

```bash
cd ~/tdtm-io
npx wrangler deploy
```

First deploy will prompt a Cloudflare login if not already authed.

## Point tdtm.io at the Worker (DNS ready)

1. Cloudflare dashboard → **Workers & Pages → tdtm-io → Settings → Domains & Routes**.
2. **Add custom domain** → `tdtm.io`, then again for `www.tdtm.io`.
3. Cloudflare creates the proxied DNS records automatically (domain must be on
   this Cloudflare account). Certs issue in a minute or two.
4. Verify: `curl -I https://tdtm.io` → `200`, and the og:image resolves at
   `https://tdtm.io/tdtm-og.png`.

## Edit

It's one file. Open `index.html`, change copy/sections, re-run `npx wrangler deploy`.
