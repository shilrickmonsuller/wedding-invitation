# Shilrick & Anna — Wedding Website

Single-page wedding invitation for GitHub Pages. Mobile-first, no build step.

## Upload to GitHub Pages
1. Put `index.html` at the root of your repository, with your images in an `assets/` folder beside it.
2. In the repo: **Settings → Pages → Source: Deploy from a branch → `main` / root**.
3. Your link will be `https://YOUR-USERNAME.github.io/YOUR-REPO/`.
4. In `index.html`, replace `YOUR-USERNAME/YOUR-REPO` in the two `og:` tags near the top so the link shows a nice preview in Messenger/Facebook.

## Files in `assets/`
Upload the whole `assets/` folder from the zip. It replaces your current one.
- Photos: couple-portrait.jpg, story-cafe.jpg, gallery-1 … gallery-12.jpg, gcash-qr.jpg
- Flowers (compressed for phones): floral-1, floral-3 … floral-7.webp, wedding-bouquet.webp
- Other: monogram.png, favicon.png, guest-attire-guide.jpg, wedding-bouquet.png (used for link previews)

These old files are no longer used and can be deleted from GitHub: floral-1 … floral-7.png, floral-2.webp (if uploaded), guest-attire-guide.png, mood1–3.jpg, reference_3.png, reference_22.png.

## Placeholders still to fill
Placeholders appear on the page with a dashed underline. Search `index.html` for `class="tbd"` to find them all:
- RSVP deadline (appears in RSVP and FAQ)
- Our Story: years/dates and the four short stories
- Schedule: guest arrival time and reception start time
- FAQ: arrival time, plus-one/children policy, parking, ceremony photo policy, contact person & number
- Venue: full street address
- Travel notes and accommodation details

Also in the `CONFIG` block at the bottom of `index.html`:
- `end` — reception end time (only used for calendar entries; currently 9:00 PM as a placeholder)
- `webhookUrl` — your n8n webhook

## RSVP (n8n)
1. Create a **Webhook** node (POST) in n8n and copy its **Production URL** into `webhookUrl`.
2. In the webhook node options, allow your GitHub Pages origin (`https://YOUR-USERNAME.github.io`) under CORS/Allowed Origins, or the browser will block the request.
3. Fields sent: `guestName`, `attendance` (Yes/No), `guestCount` (0 if declining), `contact`, `message`, `submittedAt`, `page`.
4. Connect it to Google Sheets (or similar) and activate the workflow.

Until the URL is set, guests who submit see a polite note that online RSVP isn't active yet.

## What's new in this version
- Added Our Story, Event Details & Schedule, FAQs, and Accommodations sections
- Large "Menu" button with full-screen menu on phones; floating RSVP button
- Bigger text and tap targets; attendance as large tap options; +/− guest counter
- Fixed the broken calendar button; added Google Calendar and Apple/Outlook buttons
- Waze link alongside Google Maps
- Gallery viewer with next/previous and swipe
- Opening curtain shows once per visit and is skipped for direct links (e.g. `…/#rsvp`)
- Link-preview tags, cleaned-up styles, reduced-motion support

`WORDING.md` has ready-to-use text for printed invitations, posts and messages.
