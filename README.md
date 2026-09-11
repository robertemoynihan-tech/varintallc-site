# Varinta website

A plain static website. Five HTML pages, one CSS file, one SVG icon. No framework, no
build step, no npm, nothing to compile. Whatever is in this folder is what the world sees.

---

## Files in this folder

| File | What it is |
|------|------------|
| `index.html` | Home page |
| `services.html` | How a build works, plus a pricing placeholder |
| `about.html` | Founder background |
| `security.html` | Security & Your Data |
| `contact.html` | Contact form and email link |
| `styles.css` | All styling for the whole site, including the three color palettes |
| `favicon.svg` | The little "V" icon that shows in a browser tab |
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

## Changing the color palette

Open `styles.css`. At the top there are three palette blocks. Option 1, **Ink & Sand**, is
active. Options 2 and 3 are commented out.

To switch: wrap the active `:root { ... }` block in `/*` and `*/`, then remove the `/*` and
`*/` around the one you want. Save, refresh the browser. Nothing else in the file needs to
change — every color on the site comes from those variables.

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
