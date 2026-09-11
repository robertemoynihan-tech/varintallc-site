# Placeholders — everything to fill in before go-live

Every `[PLACEHOLDER]` on the site, grouped by file. Work top to bottom and the site is done.
Search each file for the literal string `[PLACEHOLDER]` to confirm nothing is left.

---

## Site-wide (appears on all five HTML pages)

| Where | What | Notes |
|-------|------|-------|
| Footer, HTML comment on the copyright line | Legal entity name | Currently reads "© 2026 Varinta." Change to "Varinta LLC" (or whichever suffix you settle on) once the Articles of Organization are filed. Must be updated in **all five** HTML files. |

Also site-wide, not marked as placeholders but check before launch:

- The copyright year is hard-coded as **2026** in all five footers.
- Open Graph `og:image` on every page points to `https://varintallc.com/favicon.svg`. A proper
  1200×630 PNG social preview image would look far better in link previews. Optional.
- `favicon.svg` is a plain "V" mark. Replace if you commission a real logo.

---

## index.html

| Location | Placeholder | What to supply |
|----------|-------------|----------------|
| "Who this is for" section, dashed box | Client proof block | Client logos, a short testimonial, or a one-paragraph result summary. Only after the first reference build is complete **and** you have written permission to name the client. Delete the whole `.placeholder` div if you would rather ship without it than ship an empty box. |

---

## services.html

All of these sit in the dashed **Pricing** box at the bottom of the page.

| Placeholder | What to supply |
|-------------|----------------|
| Project price | Fixed price or range for a standard two-week build. Set it from tracked hours on the first reference build. |
| Discovery cost | Whether discovery is free or paid, and the amount if paid. |
| After handoff | Support window, hourly rate for changes, or optional maintenance arrangement. |
| Payment terms | Deposit, milestones, net terms. |

Once decided, replace the whole dashed block with real prose. A pricing page with a visible
"placeholder" box is worse than no pricing section at all, so delete the box if you decide
not to publish pricing.

---

## about.html

All in the dashed box near the bottom.

| Placeholder | What to supply |
|-------------|----------------|
| Founder name and headshot | Your name in the body copy and a photo. A real photo materially helps trust on a one-person site. Remember `alt` text on the image. |
| Support commitment | e.g. "response within one business day." This is an open item in your session notes — decide it. |
| Legal entity name and state | Once formation is filed. |
| LinkedIn profile URL | Or delete that line. |

---

## security.html

All in the dashed box under "A couple of things this page does not claim."

| Placeholder | What to supply | Caution |
|-------------|----------------|---------|
| Business insurance | Carrier and coverage summary for general liability / errors & omissions. | **Do not publish until a policy actually exists.** |
| NDA + MSA | Link to a standard mutual NDA and master services agreement, reviewed by a California attorney. | Your notes already flag the attorney review as a pre-first-paying-client item. |
| Service account address | The real address clients share folders with, e.g. `tools@varinta-prod.iam.gserviceaccount.com`. | Add once the Google Cloud project exists. |
| Data handling summary | A short written document a client's IT person or compliance officer can review. | Could be a linked PDF. |
| Regulated data | Specific handling arrangement, only if a project ever touches health/payment data. | State the specific arrangement. Never make a general compliance claim. |

**Rule for this page:** no invented certifications, compliance claims (SOC 2, HIPAA, ISO),
insurance, or audit history. Everything currently on the page is verifiable by the client
themselves. Keep it that way.

---

## contact.html

| Location | Placeholder | What to supply |
|----------|-------------|----------------|
| `<form action="...">` | `[PLACEHOLDER_FORM_ENDPOINT]` | Your Formspree endpoint, e.g. `https://formspree.io/f/xxxxxxxx`. Create a free form at formspree.io. Any equivalent service (Basin, Getform, Netlify Forms) works — swap the action URL. **The form silently fails until this is set.** Submit it once yourself to confirm. |
| Mailto link, two places | `[PLACEHOLDER_EMAIL]` | Your business email. It appears twice on the same line — in the `href="mailto:..."` and as the visible link text. Replace both. |
| "Response time" row | Response commitment | Same answer as the About page. Keep them consistent. |
| "Phone" row | Business phone number | Or delete that `<div>` from the `<dl>`. |
| "LinkedIn" row | Profile URL | Or delete that `<div>`. |

---

## Not placeholders, but decisions still open (from the session notes)

These do not block the site from working, but they affect what it should say:

- Suffix: Varinta LLC / Works / Group — determines the footer entity name.
- BizFile Online and USPTO TESS name searches — do these before the site is public.
- `varintallc.com` purchase — required before go-live.
- The one painful problem to lead the multi-location pitch with. If you pick it, the home
  page headline and the "What the tools do" cards should be rewritten around it. Right now
  they are deliberately general.
- Vertical choice. If you commit to one industry, the whole site gets stronger by naming it.

---

## Final sweep

From this folder, a quick check that nothing was missed:

```
grep -rn "PLACEHOLDER" *.html
```

On Windows PowerShell:

```
Select-String -Path *.html -Pattern "PLACEHOLDER"
```

Zero results means the site is ready to publish.
