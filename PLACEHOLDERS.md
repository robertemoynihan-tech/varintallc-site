# Placeholders — everything to fill in before go-live

Every `[PLACEHOLDER]` on the site, grouped by file. Work top to bottom and the site is done.
Search each file for the literal string `PLACEHOLDER` to confirm nothing is left. Note that a
few placeholders are HTML comments rather than visible blocks — the search below finds those too.

---

## Site-wide (appears on all five HTML pages)

| Where | What | Notes |
|-------|------|-------|
| Footer, email line | `[PLACEHOLDER_EMAIL]` | Your business email. It appears **twice per page** in the footer — once in the `href="mailto:..."` and once as the visible link text. Replace both, in all five files. |
| Footer, HTML comment on the entity line | Legal entity name | The footer now reads "Varinta LLC · San Diego". Confirm the suffix once the Articles of Organization are filed, and change it in **all five** HTML files if it is not "LLC". |

Also site-wide, not marked as placeholders but check before launch:

- Open Graph `og:image` on every page points to `https://varintallc.com/favicon.svg`. A proper
  1200×630 PNG social preview image would look far better in link previews. Optional. If you
  make one, use the site's own colors: graphite `#12141a` ground, parchment `#e8e4da` wordmark.
- `favicon.svg` is a plain brass "V" on graphite, recolored to match the site. Replace if you
  commission a real logo.
- The footer no longer carries a copyright line or a tagline. That is deliberate — nothing to
  update each January.

---

## index.html

The home page carries **no visible placeholder box**, on purpose: a dashed "placeholder" panel on
the first screen a prospect sees does more harm than an absent section.

| Location | Placeholder | What to supply |
|----------|-------------|----------------|
| HTML comment after the last `</section>` | Client proof | Client logos, a short testimonial, or a one-paragraph result summary, added as a fourth section. Only after the first reference build is complete **and** you have written permission to name the client. If you never add it, delete the comment. |

---

## services.html

No placeholders. The pricing section was removed on 2026-09-11 by decision; pricing is quoted per scope. If pricing is ever published, add a plain-prose section rather than a placeholder box.

-------------|----------------|
| Project price | Fixed price or range for a standard two-week build. Set it from tracked hours on the first reference build. |
| Discovery cost | Whether discovery is free or paid, and the amount if paid. |
| After handoff | Support window, hourly rate for changes, or optional maintenance arrangement. |
| Payment terms | Deposit, milestones, net terms. |

Once decided, replace the whole dashed block with plain prose. A pricing section with a visible
"placeholder" box is worse than no pricing section at all, so delete the box if you decide not to
publish pricing. The call-to-action link below it stays either way.

---

## about.html

The About page is a signed letter. Two dashed boxes sit inside and below it.

| Placeholder | What to supply |
|-------------|----------------|
| `[PLACEHOLDER: photo]` | Headshot, placed directly above the "Robert Moynihan" signature. A real photo materially helps trust on a one-person site. Remember `alt` text on the image — something like `alt="Robert Moynihan"`. |
| Support commitment | e.g. "response within one business day." Keep it consistent with the Response time row on the Contact page. |
| Legal entity name and state | Once formation is filed. |
| LinkedIn profile URL | Or delete that line. |

The founder name is no longer a placeholder — it is set in the signature block.

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
| "Or email directly" paragraph | `[PLACEHOLDER_EMAIL]` | Your business email, twice on the same line — `href="mailto:..."` and the visible text. This is in addition to the two in the footer. |
| "Response time" row | Response commitment | Same answer as the About page. Keep them consistent. |
| "Phone" row | Business phone number | Or delete that `<div>` from the `<dl>`. |
| "LinkedIn" row | Profile URL | Or delete that `<div>`. |

---

## Standing copy rules (do not break these when filling placeholders)

- No invented clients, testimonials, metrics, pricing, or certifications.
- Never reintroduce any "free to run / no tokens / costs you nothing" claim. A client may well
  pay an outside API or service provider directly; the accurate statement is the one already on
  the site — there is **no Varinta subscription**, and if a tool needs an outside service account
  it is opened in the client's name and they see the bill.
- Keep the words "hard-coded" where they appear. That word is the positioning.
- Home page prose stays short. It is currently about 120 words outside the nav and footer, and
  that is the budget.

---

## Not placeholders, but decisions still open (from the session notes)

These do not block the site from working, but they affect what it should say:

- Suffix: Varinta LLC / Works / Group — determines the footer entity name.
- BizFile Online and USPTO TESS name searches — do these before the site is public.
- The one painful problem to lead the multi-location pitch with. If you pick it, the home page
  headline and the four rows under "What Varinta builds" should be rewritten around it. Right now
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

The only remaining hit should be the intentional client-proof comment in `index.html`, if you
have chosen to leave it there.
