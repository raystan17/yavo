# YAVO site delivery

Brand picked by owner: **YAVO** (yavo.ca). Positioning and copy approved by owner before build.
Stack: static HTML, no build step. Deploy: push this folder to GitHub, import to Vercel, connect yavo.ca from Porkbun.

## Files delivered
- `index.html` : public one page site (hero, problem, free checkup form, includes, missed call text back demo, comparison, prices, how it works, proof, concept gallery, FAQ, final CTA, sticky mobile bar)
- `privacy.html` : PIPEDA style privacy policy with placeholders
- `thanks.html` : form thank you page, noindex
- `demo-private-template/index.html` : private per prospect demo template, noindex meta, X-Robots-Tag in `vercel.json`, disallowed in `robots.txt`
- `assets/morgan/` : real Morgan Exterior Solutions photos only, all WebP under 300 KB
- `robots.txt`, `sitemap.xml`, `vercel.json`

## Placeholders the owner must fill before launch
1. Form inbox: connected Nov 6, 2026 to `colesales@proton.me` via **FlowForm** (`https://flowform.to/colesales@proton.me`). Owner rule: FlowForm is what works, do NOT use FormSubmit. A live test POST on Nov 6, 2026 returned HTTP 200 `{"success":true}`. Check the Proton inbox for the test message. Standing rules saved in the owner notes.
2. Domain: `yavo.ca` was not resolving, so canonical, Open Graph and sitemap URLs temporarily point to `https://yavo-web.vercel.app/` (updated Nov 6, 2026). Buy `yavo.ca` on Porkbun, connect it in Vercel, then switch those URLs back to `https://yavo.ca/` in `index.html`, `sitemap.xml` and `robots.txt`.
3. Privacy page: updated Nov 6, 2026 with contact YAVO at `colesales@proton.me` and phone `204-901-2941` (confirmed by owner Nov 6, 2026). The number is published as tap to call in the hero, sticky mobile bar, FAQ, footer and privacy page.
4. Business phone (optional): no public YAVO phone number was confirmed, so the sticky bar uses Free checkup and See prices instead of a call button. If a business number is confirmed, add a Call button and update the footer.
5. Analytics: button and form events push to `window.dataLayer` with `data-event` names. Connect Google Analytics or Tag Manager before launch if tracking is wanted, and disclose analytics in the privacy policy.
6. Morgan review quote (optional upgrade): the proof section states the verified 5.0 star fact. If a verbatim review is added, paste it word for word from Google with the reviewer name exactly as shown. Do not paraphrase it.
7. Legal clearance for the name: web conflict checks were done, but run a CIPO trademark search and a NUANS name search for YAVO before printing signs, cards or vehicle graphics.
8. French version: no text is baked into images. A future `/fr/` copy of the pages can reuse every asset. Do not machine publish French copy without a human review.

## How to edit prices (only confirmed public prices)
Prices live in three places in `index.html`: the price cards in the Packages section, the total cost FAQ answer, and the JSON-LD offers in the head. Search the file for `1500`, `79` and `199` and update all three places together.
Confirmed public prices at build time: Get Found build from $1,500 CAD, Care $79 CAD per month, Growth $199 CAD per month. Online booking and job tracking stay as ask for a quote until the owner confirms prices in writing.
Never publish: family rates for any client, minimum terms, early exit fees, or internal costs and margins. They are not in this site. Keep them out of every future edit.

## Pre launch checks still to run on the live URL
- Lighthouse on the live phone view (target 90 plus). It was not run in this build environment, so no score is claimed here.
- Submit the checkup form once and confirm the email arrives and lands on `thanks.html`.
- Tap every button on a 390 px phone: sticky bar, checkup form, before and after slider, gallery search and filters, missed call demo.
- Confirm `yavo.ca/demo-private-template/` returns the X-Robots-Tag noindex header.

## Self critique, Phase 5 (2 revision rounds done)
Scored as three readers. Below 90 meant revise.

Round 1 scores: skeptical trades owner 84, design judge 81, Toronto owner 87.
What was weak: no clear way to ask for a human callback, form felt long, no comparison against doing it yourself or hiring a large agency, concept gallery cards were plain.
Changes made: added a talk to a person FAQ plus an optional details field on the form, added the form takes about a minute note, added the Your other options comparison section, tightened gallery labelling and counts.

Round 2 scores after revision: skeptical trades owner 91, design judge 90, Toronto owner 92.
Why they pass: the free Canada wide checkup and fixed prices are understood in the first screen, ownership and leaving are answered in plain language, real Morgan photos carry the proof with concepts clearly labelled, and Brandon appears only as base and first market.
Known limit keeping scores from going higher: there is still no confirmed public phone number on the site (placeholder item 4 above), and the name still needs the legal clearance in item 7.

## One page pitch playbook (checkups first, CASL compliant outreach only)
Goal: sell the free checkup, never the website first. The demo and the checkup notes do the persuading.

Who to pitch: local service owners from the concept batch (cleaning, trades, exterior, landscaping, restaurants) whose checkup notes show a real, fixable problem: no tap to call, not phone friendly, old or missing site, no quote form.

Compliant first contact rules (CASL): only message businesses where you have consent, an existing business relationship, or a clearly published business contact address being contacted about their business role, with no prior opt out. Identify YAVO and yourself, give a working contact, and honour every stop or unsubscribe request right away and forever. No purchased consumer lists, no personal inboxes scraped from private pages, no repeated chasing. When in doubt, call or visit in person instead of emailing.

The pitch, step by step:
1. Lead with their checkup: one real finding, said kindly. Example opener: I checked how your business shows up on Google and on a phone. Your number is not tap to call, so phone customers have to copy it. I wrote up the top 3 fixes, free, want me to send it?
2. Send the one page checkup and their private concept link together. The link is unlisted and noindex. Never post their current site problems publicly.
3. On the call, open their concept on your phone, tap the call button, tap the quote form. Then open their current site and try the same thing. Let the owner feel the difference.
4. Quote only the public prices: build from $1,500 CAD, Care $79 per month, Growth $199 per month. Booking and tracking are quoted after seeing how they run jobs. Put the exact price in writing.
5. Close on ownership: your domain, your site, your photos. If you leave, you keep them.
6. If they say no, leave the free fixes, thank them, mark do not contact if they ask, and move on. One polite follow up only where CASL allows it, then stop.

Daily routine: 5 checkups prepared, 5 first contacts, every reply answered the same day, every opt out logged. Track city by city so each new city gets its own fresh concept batch before outreach starts there.

