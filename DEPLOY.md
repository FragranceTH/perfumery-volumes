# Deploy the sales page

Three files in this folder:

| File | What it is | Goes on the web? |
|---|---|---|
| `index.html` | The whole sales page, self-contained. Images and covers embedded, no build step, no other files needed. | Yes |
| `sample.pdf` | The six-page free sample (guide, families, bergamot, rose otto, oakmoss, index). | Yes |
| `DEPLOY.md` | This file. | No |

**Never put the paid volumes on the public site.** They live in your store, behind the buyer's download link. The web folder holds the page and the free sample only.

---

## Step 1 — Replace four placeholders (5 minutes)

Open `index.html` in any text editor and search for `REPLACE`. There are four:

1. `https://payhip.com/b/REPLACE-VOL1` → your Volume I product link
2. `https://payhip.com/b/REPLACE-VOL2` → your Volume II product link
3. `https://payhip.com/b/REPLACE-BOTH` → your bundle product link
4. `https://formspree.io/f/REPLACE_FORM_ID` → your form endpoint (step 4 below)

Until you replace them the buttons deliberately show an alert rather than silently failing. Replace all four before you share the link with anyone.

---

## Step 2 — Put it online, free

### Option A: Netlify Drop (fastest, about two minutes)

1. Go to `app.netlify.com/drop`.
2. Drag this entire folder onto the page.
3. You get a live URL immediately, something like `https://calm-dune-1234.netlify.app`.
4. Site settings → Change site name → `perfumery-materials` (or whatever you like). The free URL becomes `https://perfumery-materials.netlify.app`.

No account needed to test; make one to keep the site permanently.

### Option B: GitHub Pages (free, permanent, no bandwidth worries)

1. Create a free GitHub account.
2. New repository → name it `perfumery` → Public (required on the free plan).
3. Upload `index.html` and `sample.pdf` (drag them into the browser page, then Commit).
4. Settings → Pages → Source: Deploy from a branch → Branch: `main`, folder: `/ (root)` → Save.
5. Wait two minutes. Your URL is `https://YOURNAME.github.io/perfumery/`.

### Option C: Cloudflare Pages

1. `dash.cloudflare.com` → Workers & Pages → Create → Pages → Upload assets.
2. Name the project, drag the folder, Deploy.
3. URL: `https://perfumery.pages.dev`.

### Option D: Carrd

Carrd cannot import an HTML file, so this means rebuilding by hand: one hero section, three price cards, one email form, one FAQ block. It is 20 minutes of retyping and you lose the contents section and the sample spread. Only worth it if you specifically want a Carrd-hosted page. The HTML above is better on a free host.

---

## Step 3 — Sell the files (Payhip, free plan)

1. Create a free Payhip account.
2. Add product → Digital download → upload `perfumery-vol1-craft.pdf`. Title: *Perfumery: The Complete Manual*. Price: 29 USD. Publish.
3. Repeat for `material-codex-vol2.pdf` at 39 USD.
4. Create a third product, *Both volumes*, at 59 USD, and attach both PDFs to it.
5. Copy each product URL into `index.html` where the placeholders are.

Payhip charges nothing monthly and takes roughly 5% per sale. It handles card payments and tax for you as merchant of record. If you prefer Gumroad, the fee is closer to 10% but the setup is identical.

Two settings worth turning on before launch: the seven-day refund policy in your store settings, and the affiliate feature at 30–35%, which costs nothing until someone actually sells a copy for you.

---

## Step 4 — The email form (free)

Formspree free tier: 50 submissions a month, which is plenty at the start.

1. Sign up at `formspree.io`, create a new form.
2. Copy the endpoint, which looks like `https://formspree.io/f/abcdwxyz`.
3. Paste it into the `<form action="...">` in `index.html`.
4. In Formspree, add an autoresponse so the sender receives the sample link. The form already includes a hidden `_next` field pointing at `sample.pdf`, so a visitor who submits lands on the sample directly even without an autoresponse.

**If you do not want a form at all:** delete the `<form>` block. The page already contains a plain link underneath it — *Or download the six-page sample directly* — which works with no service at all. You lose the email list, which is the one thing worth keeping, so I would keep the form.

Alternatives if you outgrow 50 a month: Buttondown (free to 100 subscribers) or MailerLite (free to 1,000).

---

## Step 5 — Test before you share

Open the live URL in a private window and check, in this order:

- Click each of the three buy buttons. You should land on a Payhip checkout with the right product and price.
- Submit the form with your own email. You should either reach `sample.pdf` or receive an email.
- Open the site on a phone. The covers should stack above the headline, the price cards should be one column.
- Buy the bundle yourself with a real card, confirm the download works, then refund yourself. Do this once — broken delivery is the most expensive bug in this business.
- Confirm no button shows the placeholder alert.

---

## Running costs

| Item | Cost |
|---|---|
| Hosting (Netlify / GitHub Pages / Cloudflare) | 0 |
| Payhip | 0 monthly, ~5% per sale |
| Formspree | 0 up to 50 submissions/month |
| Domain (optional) | ~10–15 USD/year; the free subdomain is fine to launch |

Total to be live and selling: **0 USD plus the store's cut per sale.**

---

## After launch

Submit the URL to Google Search Console (free) so the page is indexed. Then do the only marketing that costs nothing: post the sample in r/DIYfragrance, Basenotes and the beginner Facebook groups, after contributing answers for a week first. Point people at the free sample, never at the checkout.
