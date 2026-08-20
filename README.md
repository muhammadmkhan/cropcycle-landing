# CropCycle — Investor Landing Page

A single-file, self-contained landing page for **CropCycle**, an agri-fintech platform connecting farmers, investors, and buyers through escrow-funded, insured, milestone-verified crop cycles.

Built as a static, dependency-free HTML file — no build step, no framework, no package manager required.

## Live demo

_Add your deployed URL here once hosted, e.g._
`https://cropcycle.netlify.app`

## What's in this repo

```
.
├── index.html     # The entire site — HTML, CSS, and JS in one file
├── og-image.jpg   # Social preview image (LinkedIn/Twitter/WhatsApp link cards)
└── README.md
```

Product screenshots (My Crops, Add Crop, Milestones Upload, Marketplace) and the favicon are embedded directly in `index.html` as base64 images, so the file is fully portable — copy it anywhere and it still renders correctly, no separate `/images` folder needed.

`og-image.jpg` is the one exception — it has to be a real, fetchable file (social platforms won't render a base64 `og:image`), so it ships as a separate file that must sit next to `index.html` at your site's root.

### Before you deploy: update the social preview URLs

`index.html` has `og:url`, `og:image`, and `twitter:image` meta tags pointing at `https://your-domain.example/`. Find-and-replace that placeholder with your real deployed URL (e.g. `https://cropcycle.netlify.app/`) once you know it — otherwise link previews on LinkedIn/Twitter/WhatsApp won't resolve.

## Sections

- Hero with investor / farmer / buyer persona switcher
- Problem statement
- How CropCycle works (3-step cycle)
- Benefits for farmers, investors, and buyers
- Trust & security features (escrow, KYC, insurance, geo-tagged milestones)
- Product screenshots gallery
- Business model
- Market opportunity (Pakistan agriculture sector)
- About the founder
- Contact form
- Footer

## Run it locally

No install, no server required — just open the file:

```bash
open index.html        # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

Or serve it with any static file server if you want to test on a real `http://` origin:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Because this is a static site, any static host works. Deploy the whole repo (or both `index.html` and `og-image.jpg` together) — not just `index.html` alone, or the social preview image will 404.

### Netlify Drop (fastest, no account needed)
1. Go to [netlify.com/drop](https://app.netlify.com/drop)
2. Drag the folder containing `index.html` **and** `og-image.jpg` onto the page
3. You'll get a live `*.netlify.app` link instantly — create a free account afterward to claim the site and attach a custom domain
4. Come back and update the `og:url` / `og:image` / `twitter:image` meta tags in `index.html` with that real URL, then redeploy

### GitHub Pages
1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to the `main` branch, root folder
4. Site goes live at `https://<username>.github.io/<repo-name>`

### Vercel / Cloudflare Pages
Same idea — connect the repo (or drag-and-drop the file) and deploy. No build command needed.

## Customizing

Everything lives in `index.html`:

- **Colors & type** — CSS custom properties at the top of the `<style>` block (`--paper`, `--ink`, `--green`, `--amber`, fonts loaded from Google Fonts)
- **Copy** — plain HTML, edit directly in each `<section>`
- **Stats / numbers** — market opportunity figures are sourced from the Pakistan Economic Survey 2024–25 and public research; update the source note in the Market section if you change them
- **Screenshots** — swap the base64 strings in the `<script>` block near the bottom (`IMG_MYCROPS`, `IMG_ADDCROP1`, etc.) with new images re-encoded the same way

## Known limitations

- **Contact form is front-end only.** It shows a success message on submit but doesn't send anywhere yet. To make it functional:
  - On Netlify: add `data-netlify="true"` and a hidden `form-name` input to the `<form>` tag — Netlify Forms will pick it up automatically, no backend needed
  - Elsewhere: point the form at a service like Formspree, or a small serverless function
- All portfolio/product data shown (ROI %, payouts, transparency scores) is illustrative, not live data
- No analytics or cookie consent included — add before public launch if needed

## Disclaimer

CropCycle is a technology platform in pre-seed development. This page is a marketing prototype; figures and screens shown are illustrative of the product roadmap and do not constitute an offer to sell securities or investment products.

## Repo settings (GitHub)

On the repo page, click the ⚙️ gear next to **About** and set:

- **Description:** `Investor landing page for CropCycle — an agri-fintech platform connecting farmers, investors, and buyers through escrow-funded, insured crop cycles.`
- **Website:** your deployed URL, once live
- **Topics:** `agri-fintech` `agritech` `landing-page` `fintech` `pakistan` `static-site` `html-css-js`

This is also what shows up in the social preview card when the repo link itself is shared, separate from the `index.html` OG tags above.

## License

Add a license of your choice (MIT, proprietary, etc.) before making this repo public.
