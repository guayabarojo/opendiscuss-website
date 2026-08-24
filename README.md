# opendiscuss-website

Static landing page for **opendiscuss.ai**. Plain HTML + CSS — no framework, no build step.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The entire site. Also hosts the CRM tracker snippet. |
| `styles.css` | All styling. CSS custom properties at the top control the palette. |
| `favicon.svg` | Tab icon / brand mark. |

## Run locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploys

Vercel is connected to this repo's GitHub remote. **Every push to `main` deploys
automatically** — there is no build command; Vercel serves the repo root as static files.

Pull requests get their own preview URL.

## CRM tracker

The VBT.io visitor-tracking embed (account `VBT-76761-15875`) lives at the **bottom of
`index.html`, just before `</body>`**, wrapped in an HTML comment identifying it.

It is pasted exactly as the vendor supplied it. Don't hand-edit it — if the account or
domain changes, get a fresh snippet from the vendor and replace the whole block.

Two things to know:

- The snippet is registered against `https://opendiscuss.ai`. It may not report hits from
  `*.vercel.app` preview URLs, since vendor trackers commonly filter on the registered
  domain. Test against the real domain.
- If you add more pages later, the snippet must be copied into each one — it is per-page.

To verify it's firing: load the site, open DevTools → Network, filter for `vbt`, and look
for a request to `www.vbt.io/tracker?_account=VBT-76761-15875&...`.

## Domain

`opendiscuss.ai` and `www.opendiscuss.ai` are configured under the Vercel project's
Settings → Domains. DNS records live at the registrar; Vercel's Domains tab shows the
exact values it expects, and issues HTTPS automatically once they resolve.
