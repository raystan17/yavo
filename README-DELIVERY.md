# YAVO website. Delivery notes

Static site. No build step, no framework, no dependencies. Everything that ships is plain HTML, CSS, JavaScript, fonts and images in this folder.

Live: https://yavo-web.vercel.app/

## What is in the folder

| Path | What it is |
| --- | --- |
| `index.html` | The homepage. All styles and scripts are inline in this one file. |
| `privacy.html` | Privacy policy (PIPEDA). Linked from the form consent text and the footer. |
| `thanks.html` | Fallback thank-you page. Only reached if the browser cannot submit the form with JavaScript. `noindex`. |
| `examples/<slug>/` | Twelve complete example websites for fictional businesses. Each is a full site with its own `assets/` folder. Linked from the example gallery. `noindex`. |
| `assets/examples/` | Gallery thumbnails. `<slug>.webp` (960 wide), `<slug>-md.webp` (720), `<slug>-sm.webp` (480), plus `phone-clearwater*.webp` for the hero phone mock. |
| `assets/brand/` | Logo kit. See below. |
| `assets/fonts/` | Self-hosted fonts (Bricolage Grotesque for headings, Instrument Sans for body). OFL licensed, subset and instanced to keep them small. |
| `assets/morgan/` | Real before and after photos from the Morgan Exterior Solutions job, used in the proof section. |
| `demo-private-template/` | Blank template for private concept previews sent to one prospect. Not linked anywhere. `noindex`. |
| `vercel.json` | Headers (security, caching, `X-Robots-Tag: noindex` for examples, thanks page and private template) and `trailingSlash`. |
| `robots.txt`, `sitemap.xml`, `site.webmanifest` | Crawl rules, sitemap (homepage and privacy only), PWA manifest for the icons. |

## Deploy

The site deploys from GitHub to Vercel automatically.

1. Make your edit.
2. `git add -A`
3. `git commit -m "Describe the change"`
4. `git push origin main`

`origin` pushes to both `raystan17/yavo` and `raystan17/yavo-web`. Vercel builds from the push within a minute or two. There is nothing to compile. If you ever need to deploy by hand, `npx vercel --prod` from this folder works too.

To preview locally, open `index.html` in a browser, or run any static server from this folder (for example `npx serve .`). Root-relative links such as `/examples/...` need a server, so use the server if you are checking the gallery.

## Change the prices

Prices appear in three places. Keep them matching.

1. **Price cards** in `index.html`, section `id="prices"`. Search for `class="amt"`. There are three: `$1,500`, `$79` and `$199`. The small text under each (`per month`, `one time, from`) is next to it.
2. **FAQ answer** in `index.html`, section `id="faq"`. The first question, `How much will this cost me, in total?`, repeats the prices as plain text.
3. **Structured data** near the top of `index.html` inside `<script type="application/ld+json">`. Search for `"price":"1500"`, `"price":"79"` and `"price":"199"`. Google reads these, so update them too.

Booking systems and job tracking are deliberately "ask for a quote". Do not add a public price for them unless you are ready to honour it for everyone.

## Change the phone number or email

Search `index.html`, `privacy.html` and `thanks.html` for `204-901-2941`, `+12049012941` and `colesales@proton.me`. Replace all occurrences. The sticky mobile bar, header, footer, FAQ, form fallback text and structured data all use them.

## The checkup form

- Posts to FlowForm: `https://flowform.to/colesales@proton.me`. Never switch this to FormSubmit.
- JavaScript submits in the background and shows an inline success message. If that fails with a network error, the browser falls back to a normal form post and FlowForm redirects to `/thanks.html`. If FlowForm answers with an error, the inline error message with the email and phone fallback appears.
- Fields sent: name, phone, email, business, city, website, need, details, consent (yes), style (the example style the visitor picked, if any), `_subject`, `_source`.
- The consent checkbox is required. Its wording and the privacy page together cover PIPEDA.
- Tested end to end on 6 Nov 2026: FlowForm returned HTTP 200 and the inline success state showed.

If FlowForm asks you to confirm the inbox the first time a message arrives, open the email from FlowForm and click the confirm link once.

## Analytics

Every tracked element has a `data-event` attribute, and the page pushes `{event, ...}` objects into `window.dataLayer`. Nothing else is installed. To turn on Google Analytics, add the GA4 or Google Tag Manager snippet in the `<head>` of `index.html` and the existing events will flow through.

## The example gallery

The gallery is driven by the `examples` array in the script at the bottom of `index.html`. Each entry is one card:

```js
{slug:"clearwater-cleaning", name:"Clearwater Cleaning Co.", trade:"Home and commercial cleaning", cat:"cleaning", style:"Clean & bright", blurb:"...", kw:"search words"}
```

To add an example:

1. Build the site in `examples/<new-slug>/index.html`. Copy an existing one as a starting point. Keep the top banner (`Example website by YAVO. Not a live client business.` with the `Back to YAVO examples` link), the fictional business name, the `204-555-01xx` phone pattern, the town `Riverbend`, the disabled demo form and the `Sample review` labels.
2. Use only photos you have the right to publish. The current examples use Unsplash photos.
3. Take a screenshot of the top of the page at 1440 wide, crop to 960 by 600 (top aligned), save as `assets/examples/<new-slug>.webp`, plus 720 and 480 wide copies named `-md` and `-sm`.
4. Add the entry to the `examples` array. `cat` must be one of `cleaning`, `trades`, `property`, `auto`, `food` (these are the filter buttons; labels live in `catLabel`).

Rules that keep the gallery honest: every card must open a real working page, no card may describe a real client, and nothing in an example may claim results.

Philco Cleaning and Ray's Cleaning are shown separately as a custom design demo and an early practice concept. They are not clients and are not counted as proof. If either URL ever stops working, remove its card.

## Logo kit (`assets/brand/`)

| File | Use |
| --- | --- |
| `yavo-logo.svg` | Primary wordmark with the orange dot. Navy on light backgrounds. |
| `yavo-logo-white.svg` | Same, white, for navy or dark backgrounds. |
| `yavo-logo-mono.svg`, `yavo-logo-mono-white.svg` | Single colour versions for print, embroidery, invoices. |
| `yavo-lockup.svg`, `yavo-lockup-white.svg` | Wordmark with the tagline. |
| `yavo-wordmark.svg`, `yavo-wordmark-white.svg` | Wordmark without the dot. |
| `yavo-mark.svg`, `yavo-mark-white.svg`, `yavo-mark-mono.svg`, `yavo-mark-tile.svg` | The Y monogram alone. Tile version has the navy rounded square behind it. |
| `favicon.svg`, `favicon-32.png` | Browser icons. |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | Home screen and manifest icons. |
| `og-card.png` | 1200 by 630 social share image. |

Colours: navy `#041E42`, orange `#FF4C00`, white `#FFFFFF`, off-white `#F4F7FB`. Orange is for the dot, the primary button, the eyebrow labels and small accents only. Buttons use white text on orange.

Fonts: Bricolage Grotesque (headings, weight 700) and Instrument Sans (body). Both are SIL Open Font License. The files in `assets/fonts/` are subset to Latin and Latin Extended and instanced (width and optical size axes removed) to keep them small. If you need other weights, download the originals from Google Fonts and re-subset.

## Placeholders and things to change later

- **Domain.** The site is set up for `https://yavo-web.vercel.app/`. When `yavo.ca` is live and pointed at Vercel, search and replace `https://yavo-web.vercel.app` across `index.html`, `privacy.html`, `thanks.html`, `sitemap.xml`, `robots.txt` and `examples/*/index.html` (the `Back to YAVO examples` link uses a root-relative `/#examples` so it does not need changing).
- **Proof.** Only Morgan Exterior Solutions appears as a real client, with permission. Add new proof only when you have a live client URL and the owner has agreed in writing. No review counts, ratings or client totals anywhere.
- **Service area.** Copy says "across Canada" with Brandon, Manitoba as the base. Change the `addressLocality` in the structured data if the base moves.
- **Privacy policy date.** Update the `Last updated` line in `privacy.html` whenever the policy changes.

## Quality checks done before launch

- Every internal link, anchor, gallery card (12 examples, Philco, Ray's, Morgan) checked at 1440 and 390 wide. No horizontal overflow, console clean.
- Filters, search, empty state, mobile "Show all" button, "Use this style" picker, FAQ, before and after slider (mouse, touch and keyboard), missed-call demo, mobile menu and sticky call bar exercised.
- Real FlowForm submission sent and received (HTTP 200).
- PageSpeed Insights, mobile, live URL, 6 Nov 2026: Performance 99, Accessibility 100, Best Practices 100, SEO 100 (LCP 1.0 s, TBT 0 ms, CLS 0). Re-check at https://pagespeed.web.dev/ after each deploy.
- No em dashes in the homepage copy. Example sites are fictional, carry the example banner, and contain no real business names, phone numbers, addresses or reviews.
