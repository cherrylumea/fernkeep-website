# Overnight Autopilot Log — fernkeep-website

## Start here (5 things for Cherry)

1. **Revision-rate pricing conflict, unresolved** — the packages footnote says "$56/hour" for extra
   revisions but the FAQ says "$75 an hour" for the same thing. I did not guess which is correct;
   pick one and I (or you) can fix both spots in `index.html`. See Task 2 below for exact lines.
2. **Footer package prices were stale** — they didn't match the founding rates shown in the
   pricing cards ($800/$1,500/$2,000/$3,200 vs. the actual $590/$1,110/$1,480/$2,370). Fixed —
   footer now matches the cards. Worth a quick glance to confirm founding rates are still current.
3. **Maria Da Silva email drafted, not sent** — see `drafts/maria-da-silva-reassurance.md`. It's
   missing her email address, the specific package/price discussed, and your sign-off details —
   I didn't have any of that in this repo and wouldn't guess it. Fill those in before sending.
4. **No repo-level blockers found** — this is a single `index.html` file, no build step, no other
   pages, no stale branches, no loose files to clean up. Repo is already tidy.
5. **Meta Ads task (item 3) is effectively N/A for this repo** — there's no ad-creative asset here
   (no images/videos), just page copy and a Meta Pixel snippet for tracking. See Task 3 for what
   I could actually check.

---

## Task 1 — Maria Da Silva reassurance email draft
**Status:** Done (drafted, NOT sent)
**Started/finished:** same session, ~10 min

Wrote a short, warm draft reframing the website as a permanent, year-round asset rather than a
seasonal purchase — directly addressing the theory that she may be treating it as tied to the
cottage's operating season.

Saved to: `drafts/maria-da-silva-reassurance.md`
Channel it's ready for: **Email** (not sent — no send action taken).

Full draft text is in that file. Left several fields as placeholders since I couldn't verify them
in this repo:
- Her email address — UNKNOWN, not present anywhere in this repo
- The specific package/price actually discussed with her — UNKNOWN, left unspecified rather than
  guessing a number from the pricing table
- Exact cottage/property name — left generic
- Sign-off/contact details — placeholder, needs Cherry's actual details

**Nothing was sent anywhere.** File is a plain markdown draft in the repo.

---

## Task 2 — Site audit (fernkeep-website / index.html)
**Status:** Partial (fixed what was safe, flagged the rest)

This is a single static `index.html` (1,188 lines, no build tooling, no other files). Checked for:
broken links, missing alt text, placeholder/lorem-ipsum content, obvious accessibility gaps, and
internal inconsistencies.

**Findings:**

- **FIXED — Footer package prices didn't match the pricing section.**
  `index.html`, footer "Working together" column (previously lines ~1001–1004):
  - Was: The Single Page — $800 / The Custom Site — $1,500 / The Presence Package — $2,000 /
    The Signature Package — $3,200
  - Pricing cards (section `#packages`, lines ~808–861) actually show founding rates of $590 /
    $1,110 / $1,480 / $2,370 (standard rates $890/$1,630/$2,070/$3,330 noted alongside).
  - I updated the footer to match the founding rates shown in the cards, since those are the
    prices actually being offered right now and the founding-rate framing is explicit and
    time-limited on the page itself. **Judgment call flagged:** if you'd rather the footer show
    standard (non-founding) rates instead, that's a one-line swap — let me know which you want
    going forward once founding rates expire.

- **NOT FIXED — revision hourly-rate inconsistency.** Two different rates appear for the same
  thing (additional revisions beyond the included rounds):
  - Line ~876, `.pkg-foot` "Revisions" note: **"$56/hour"**
  - Line ~937, FAQ "What if I do not like the design?": **"$75 an hour"**
  I did not guess which is correct — this is exactly a Cherry judgment call. **Question for
  Cherry: which rate is current, $56/hr or $75/hr?** Once you tell me, I can make both spots
  consistent.

- **Anchor links / navigation:** checked every `href="#..."` against section `id`s
  (`#gap #try #process #work #packages #questions #start #top`) — all resolve, none broken.

- **Alt text / images:** no `<img>` tags in the file at all — all graphics are inline SVG. Every
  decorative SVG group is either `aria-hidden="true"` or sits inside a link that already has
  `aria-label` (e.g. the logo link, `aria-label="Fernkeep home"`). No missing alt-text issue found.

- **Placeholder / unfinished content:** searched for "TODO", "FIXME", "lorem ipsum", "placeholder",
  "coming soon" — none found. No unfinished sections.

- **Intentional anonymization, not a bug:** the "Selected work" case study (around line 710–716)
  has an explicit HTML comment saying the client is anonymized "until the client confirms in
  writing," with instructions for how to un-anonymize later. Left as-is — this is clearly
  deliberate, not an oversight.

- **Accessibility:** `:focus-visible` styles are defined, `prefers-reduced-motion` is respected
  (animations/transitions disabled), form fields have associated `<label for>` elements, buttons
  have appropriate `aria-expanded`/`aria-pressed` states (mobile menu, FAQ accordion, palette
  swatches). No obvious a11y gaps found in markup. I did not have a browser/axe-core available in
  this environment to run an automated console/a11y scan — this was a manual code read, not a
  live-rendered check. If you want an automated Lighthouse/axe pass, that needs to run against the
  live or locally-served page.

- **Console errors:** couldn't verify at runtime (no headless browser run in this pass — manual
  code read only). Script reads clean; no obvious undefined references or syntax issues on
  inspection. `fbq` is defined in the `<head>` pixel snippet before the closing `</body>` script
  runs, so no ordering issue there.

- **`og:url` says `https://fernkeep.com`** — I have no way to verify this domain is actually live
  /owned/correct from inside this repo. Marked UNKNOWN, left as-is (not something to guess-fix).

- **Booking link:** `BOOKING_URL = "https://cal.com/fernkeep"` (line ~1032) — I cannot verify this
  Cal.com link is live/valid without an external check I'm not authorized to make unprompted here
  beyond passive reading. Flagging as UNKNOWN — worth a manual click-check.

---

## Task 3 — Meta Ads context check
**Status:** Partial / mostly N/A for this repo

There is a Meta Pixel snippet installed (`fbq('init', '1016291037675168')`, PageView + Lead +
ViewContent events tracked on CTA clicks and the demo "Publish" button) — that's the only
ads-adjacent asset actually in this repo. There is **no image or video creative** in this repo at
all (everything on the page is CSS/SVG, no photography, no ad copy variants, no landing-page
sections built specifically for ad traffic).

So, regarding the specific recommendation (vertical 9:16 Reels-format creative for a 45+
audience): there's nothing here to evaluate for mobile/vertical optimization — no creative assets
exist in this repo to check. That work (sourcing/producing a vertical video asset) is outside what
this repo contains, and I did not create or launch any ad creative, per the boundaries.

**One relevant observation on the landing page itself:** the page's own responsive design is
already mobile-first friendly (fluid type via `clamp()`, single-column stacking below ~900px,
large tap targets ≥44px on buttons), so *if* this page is ever used as an ad-click landing
destination, it should render reasonably on mobile. But that's about the landing page, not the ad
creative itself — no action taken, no creative built.

---

## Task 4 — General cleanup
**Status:** Done — nothing to clean up

- Repo contents: `index.html` only, plus the two new folders I created (`drafts/`, `_to_review/`,
  currently empty).
- Branches: `main` and `claude/festive-archimedes-qo9ygr`, both at the same single commit
  ("Initial commit: fernkeep website with USD pricing and Meta Pixel"). No stale or duplicate
  branches to flag.
- No loose/unused files found anywhere in the working tree.

---

## Summary of changes made
- `index.html`: footer package prices corrected to match the founding rates shown in the pricing
  section (see Task 2).
- `drafts/maria-da-silva-reassurance.md`: new file, draft email, not sent.
- `_to_review/`: created, empty (nothing needed moving into it).

No commits pushed to a remote beyond the working branch `claude/festive-archimedes-qo9ygr` per
standing repo instructions; no publish/deploy action taken; nothing sent to any person or service.
