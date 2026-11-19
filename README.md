# PlusSizeBeauty: site v1

This is one static page with no build step and no backend. Products come from a published Google Sheet. Until a sheet is connected, it falls back to the sample products in `index.html`.

## Setup (for Jarrett, ~30 min)

1. **Sheet:** Create a Google Sheet in *his* Google account and import `products-template.csv` (File → Import). Keep the header row exactly as it is.
2. **Publish it:** File → Share → Publish to web → choose that tab → **CSV** → Publish. Copy the URL.
3. **Wire it up:** Paste that URL into `SHEET_CSV_URL` near the bottom of `index.html`.
4. **Deploy:** Drag the folder into Cloudflare Pages or Netlify (both have free drag-and-drop deploys). The page fetches the sheet on every load, so edits to the sheet go live within a few minutes (Google caches the published CSV briefly) without a redeploy.
5. **Domain:** Add the custom domain in the host's dashboard, then set the DNS records it asks for at his registrar.
6. **Before launch:** Replace the About text (it's in `[brackets]`) and the `hello@example.com` contact email. Replace `images/hero-banner.jpg` with the full-size banner. The current one is cropped from a screenshot, so faces are cut off at the bottom; a same-named file drops right in.

### Columns

| Column | What goes in it |
|---|---|
| name | Product name |
| price | `45` or `$45` |
| section | Fashion, Beauty, Skin Care, or Hair Care. This controls which menu tab the item shows under. |
| category | Small label on the card (Dresses, Serums…). Optional. |
| image | A direct image URL from the affiliate program |
| link | The affiliate link |
| store | The store name, shown under the button |
| active | `no` hides the item without deleting the row |

---

## How to update the website (for him)

**You only ever edit the spreadsheet. You never need to touch the website itself.**

**To add a product:**
1. Open the spreadsheet.
2. Go to the first empty row at the bottom.
3. Fill in each box: the name, the price, the **section** (Fashion, Beauty, Skin Care, or Hair Care — spelled exactly like that), the type (like *Dresses*), the picture link, the shopping link, and the store name.
4. Refresh the website after a few minutes. Your product will be there.

**To remove a product:** Type `no` in the **active** box for that row. To bring it back, change it to `yes`.

**Tips**
- Spell the section exactly the same every time. If it's misspelled, the item gets its own extra tab.
- Don't change or delete the first row (the titles).
- If a picture doesn't show up, the picture link is probably wrong. Right-click the product image on the store's site and choose "Copy image address."
