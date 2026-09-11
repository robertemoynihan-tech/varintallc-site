# Varinta LLC website

**Current deployment (2026-09-11):** GitHub Pages from https://github.com/robertemoynihan-tech/varintallc-site (branch `main`, root). This folder is that git repo. To publish a change:

```
git add -A
git commit -m "describe the change"
git push
```

Pages rebuilds in about a minute. Custom domain is set to varintallc.com via the `CNAME` file (do not delete it). DNS lives at Squarespace Domains; records required are in the "GitHub Pages DNS" section below. After DNS resolves, turn on **Enforce HTTPS** in the repo's Settings → Pages.

## GitHub Pages DNS (Squarespace Domains → DNS settings → Custom records)

| Type | Host | Data |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | robertemoynihan-tech.github.io |

Delete any pre-existing Squarespace A records on `@` (198.185.159.x / 198.49.23.x) and any Squarespace CNAME on `www`, or the site will keep landing on Squarespace's parking page.

---

The Netlify / Cloudflare Pages instructions below are kept as alternatives.

# Varinta website

A plain static website. Five HTML pages, one CSS file, one SVG icon. No framework, no
build step, no npm, nothing to compile. Whatever is in this folder is what the world sees.

---

## Files in this folder

| File | What it is |
|------|------------|
| `index.html` | Home page |
| `services.html` | How a build works, plus a pricing placeholder |
| `about.html` | A signed letter from the founder — the one first-person page |
| `security.html` | Security & Your Data |
| `contact.html` | Contact form and email link |
| `styles.css` | All styling for the whole site, including the three color palettes. No JavaScript file exists, by design — see **Design system** below |
| `favicon.svg` | The little brass "V" icon that shows in a browser tab |
| `sitemap.xml` | Tells search engines which pages exist |
| `robots.txt` | Tells search engines they are welcome |
| `PLACEHOLDERS.md` | Every `[PLACEHOLDER]` on the site, in one list |
| `README.md` | This file |

`PLACEHOLDERS.md` and `README.md` are notes for you. They get uploaded with everything
else and that is harmless — nobody will find them unless they guess the filename. If you
would rather they not be public at all, delete them from the deployed copy and keep them
somewhere else.

---

## Domain: varintallc.com (purchased 2026-09-11)

**`varintallc.com` is already registered.** Log in to the registrar you bought it from to change the DNS records described below. Nothing below about custom
domains will work until you own it.

Buy it from any registrar — Cloudflare Registrar, Namecheap, Porkbun, or Google Domains'
successor Squarespace Domains all work. Expect roughly $10–$15 per year for a `.com`.
Turn on auto-renew and turn on WHOIS privacy (usually free) so your home address is not
published in a public database.

One convenience note: if you buy the domain **at Cloudflare** and host the site on
**Cloudflare Pages**, the DNS step below happens automatically and you can skip most of it.
That is the path with the fewest moving parts.

---

## Viewing the site on your own computer first

Just double-click `index.html`. It opens in your browser and everything works, because
there is no server-side code. Every link between pages works too.

---

## Option A — Deploy to Netlify

### A1. Drag and drop (fastest, no Git needed)

1. Go to **https://app.netlify.com** and create a free account.
2. On the dashboard, find the box that says **"Drag and drop your site output folder here"**
   (it may be under **Sites → Add new site → Deploy manually**).
3. Drag this entire `website` folder onto that box. Drag the **folder**, not the files
   inside it.
4. Wait about ten seconds. Netlify gives you a live URL like
   `https://curious-otter-a1b2c3.netlify.app`. Click it — that is your site, already public.
5. To update the site later, drag the folder onto the same place again. It replaces the old
   version.

The random name is normal. You can change it under **Site configuration → Change site name**,
and it stops mattering entirely once you connect `varintallc.com`.

### A2. From Git (better once you are making regular changes)

1. Put this folder in a GitHub repository (GitHub Desktop is the easiest way if you have not
   used Git before).
2. In Netlify: **Add new site → Import an existing project → GitHub**, and authorize it.
3. Pick the repository.
4. When it asks for build settings, leave them empty:
   - **Build command:** leave blank
   - **Publish directory:** `/` if the HTML files are at the top of the repo, or `website`
     if this folder sits inside a larger repo.
5. Click **Deploy**.

From then on, every time you push a change to GitHub, Netlify republishes within a minute.

### A3. Point varintallc.com at Netlify

1. In your site: **Domain management → Add a domain** → type `varintallc.com` → **Verify** →
   **Add domain**.
2. Netlify will show you DNS records to create. Two approaches:

   **Easiest — let Netlify run DNS.** Netlify offers to use "Netlify DNS" and gives you four
   nameservers, like `dns1.p01.nsone.net`. Go to your registrar, find **Nameservers**, choose
   the custom/"use my own" option, and paste in all four, replacing what is there. Save.

   **Or — keep DNS at your registrar.** In your registrar's DNS panel, create:

   | Type | Name / Host | Value |
   |------|-------------|-------|
   | A | `@` | `75.2.60.5` |
   | CNAME | `www` | `your-site-name.netlify.app` |

   `@` means the bare domain `varintallc.com` itself. Confirm the A record IP against what
   Netlify shows you on screen — it is the authoritative source and can change.

3. Wait. DNS changes take anywhere from a few minutes to a few hours to spread across the
   internet (up to 48 hours in the worst case, though it is usually well under one).
4. Netlify issues a free HTTPS certificate automatically once DNS resolves. You do not have
   to buy one. If the padlock does not appear after DNS is live, go to
   **Domain management → HTTPS → Verify DNS configuration** and then **Provision certificate**.

---

## Option B — Deploy to Cloudflare Pages

### B1. Drag and drop

1. Create a free account at **https://dash.cloudflare.com**.
2. In the sidebar: **Workers & Pages → Create → Pages → Upload assets**.
3. Give the project a name, for example `varinta`.
4. Drag this `website` folder in, or click to select it, then **Deploy site**.
5. You get a live URL like `https://varinta.pages.dev`.
6. To update later: open the project, go to **Create deployment**, and upload the folder again.

### B2. From Git

1. Put the folder in a GitHub repository.
2. **Workers & Pages → Create → Pages → Connect to Git**, authorize GitHub, pick the repo.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** leave blank
   - **Build output directory:** `/` (or `website` if this folder sits inside a larger repo)
4. **Save and Deploy.** Every push to GitHub republishes automatically.

### B3. Point varintallc.com at Cloudflare Pages

**If you bought the domain at Cloudflare:** open your Pages project → **Custom domains →
Set up a custom domain** → type `varintallc.com` → confirm. Cloudflare creates the DNS records
itself. You are done.

**If the domain is at another registrar,** the normal path is to move DNS management to
Cloudflare (you do not have to move the registration itself):

1. In Cloudflare: **Add a site** → enter `varintallc.com` → choose the **Free** plan.
2. Cloudflare scans your existing records and gives you two nameservers, like
   `ana.ns.cloudflare.com` and `bob.ns.cloudflare.com`.
3. At your registrar, replace the existing nameservers with those two. Save.
4. Wait for Cloudflare to report the domain as **Active** (minutes to a few hours).
5. Back in your Pages project: **Custom domains → Set up a custom domain** → `varintallc.com`.
   Repeat for `www.varintallc.com` if you want both to work.

HTTPS is automatic and free here as well.

---

## Which should you pick?

Either is fine and both are free at this size. Netlify's drag-and-drop is slightly friendlier
the very first time. Cloudflare is the tidier choice if you also buy the domain there, since
DNS configures itself. You can switch later by repointing DNS.

---

## What to expect after you point the domain

- **It will not be instant.** DNS propagation is normal and can take a few hours. Do not
  assume you broke something in the first thirty minutes.
- **You may see the old page or an error while it propagates.** Try a different device or a
  phone on cell data — your own computer caches DNS aggressively.
- **The padlock may lag the domain.** The certificate is issued after DNS resolves, so a
  brief "not secure" warning right after cutover is expected. If it persists for more than a
  few hours, look for a "verify DNS" or "provision certificate" button in the host's dashboard.
- **Both `varintallc.com` and `www.varintallc.com` should work.** Set up both; the host will
  redirect one to the other.

---

## Design system

The look is meant to read as an old-line private client firm: dark, quiet, expensive, and above
all **familiar**. The audience is small-business owners who are not looking for a novel web
experience. Everything below exists to make the site behave the way they already expect a
website to behave.

### Palette

All color lives in CSS custom properties at the very top of `styles.css`. There are three
palettes; one is active.

| Palette | Ground | Accent | When to use |
|---|---|---|---|
| **Graphite & Brass** (active) | `#12141a` graphite | `#8b5e34` aged brass, `#b07a45` for links | The default. |
| **Oxblood** | same graphite | `#7a2b2b`, `#c86a6a` for links | If the brass ever reads too warm. |
| **Ivory** | `#f4f1ea` parchment | same brass | Light escape hatch if the dark site reads as too severe for a particular audience. |

**To switch:** wrap the active `:root { ... }` block in `/*` and `*/`, then delete the `/*` and
`*/` around the block you want. Save, refresh. Nothing else needs to change — every color on
the site comes from those variables.

Contrast was measured, not eyeballed. Body text `#e8e4da` on graphite is **14.5:1**, muted text
`#9a9daa` is **6.8:1**, and link brass `#b07a45` is **5.0:1** on the page background and
**4.5:1** on the recessed form-field surface. All pass WCAG AA for body-size text. The full brass
`#8b5e34` measures only 3.3:1, so it is used for rules, borders, and the nav underline — never
for text. The same check is why the Oxblood palette's link color is lightened to `#c86a6a`; the
obvious `#b04848` only reaches 3.4:1.

### Type

Two families, loaded from Google Fonts with one stylesheet request plus two `preconnect` hints:

- **Playfair Display** 500/600 — the wordmark, h1, h2, h3, and definition-list labels. Falls back
  to Georgia.
- **Inter** 400/600 — body, nav, forms, eyebrow labels. Falls back to the system sans stack.

Body text is 18px on desktop, 17px on mobile, line-height 1.6, and the measure is capped at 66
characters. Headlines are large relative to the body (2.75rem / 2rem for h1) at weight 500 — the
size does the work, not weight or capitals. Numerals are old-style by default.

### Structure

No cards, no boxes, no shadows, no gradients, no rounded corners. Structure comes from 1px
hairline rules in `--color-rule` and from generous vertical padding (5rem desktop, 3rem mobile).
"What you get" content uses two-column definition lists — label left, sentence right — because
that reads as a printed prospectus rather than a SaaS feature grid.

Each page has **exactly one** call to action, styled as an underlined text link in the accent
color with a trailing arrow. The only button on the site is the contact form's submit: a flat
rectangle with a 1px accent border that fills on hover.

### The no-animation rule

There is no JavaScript anywhere on this site, and nothing on it moves. No transitions except a
flat color change on `:hover` and `:focus`, no scroll reveals, no parallax, no sticky or fixed
header, no hamburger menu. Below 640px the nav simply stacks into a plain always-visible list —
there is no toggle to discover.

This is not minimalism for its own sake. The client base is older owners who are being asked to
trust a stranger with access to their email and files. Motion reads as marketing; a page that
sits still reads as a document. It is also the most robust possible version of the site: it works
with JavaScript disabled, on an old browser, on a bad connection, and with a screen reader,
and there is nothing to break. If you edit the CSS later, keep it that way — the rule is written
at the top of `styles.css` as well.

### Accessibility contract

Every page has a skip link, `aria-current="page"` on the active nav item, semantic landmarks,
visible focus rings, and links that are always underlined. Keep all five of those if you change
anything.

---

## Before you go live — checklist

1. `varintallc.com` is already purchased; have your registrar login ready.
2. Work through `PLACEHOLDERS.md` and replace every `[PLACEHOLDER]`.
3. Set the real form endpoint in `contact.html` (create a free form at
   https://formspree.io, which gives you a URL to paste in) and the real email address.
4. Submit the form once yourself to confirm it arrives.
5. Click every link on every page.
6. Open the site on a phone.
7. After the domain is live, submit `https://varintallc.com/sitemap.xml` to Google Search
   Console so the site starts getting indexed.
