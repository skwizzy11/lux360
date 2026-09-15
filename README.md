# Lux360 Clean — landing page

A single-page replacement for `lux360clean.com` (currently Squarespace). One HTML file,
inline CSS and JS, two self-hosted font files, no framework and no build step.

```
index.html   the whole page: markup, styles, script, JSON-LD
fonts.css    @font-face only
fonts/       Libre Franklin variable roman, latin + latin-ext subsets (woff2)
img/         photographs, all from the client's own site
favicon.svg / favicon.png / apple-touch-icon.png / og.jpg
robots.txt   sitemap line points at a sitemap that does not exist yet
404.html
```

Open `index.html` over HTTP, not `file://` — the font files need a real origin.

---

## 1. Confirm before publishing

**In order. The first one blocks launch.**

1. **Which city.** The live site says *"Osage Beach, Lake Ozark & Surrounding Areas"* in
   the footer and the H1 of every page. That is Missouri. Against it: the phone number is
   **512**, which is Austin; the Yelp listing is **The Hills, TX**, a village next to
   Lakeway; and the client's own hero filename is `…Luxury Cleaning Services in Austin`.
   Three independent signals to one, so this page is built for **Austin and the western
   suburbs (The Hills, Lakeway, Bee Cave, Westlake)**. That decision is baked into the
   `<title>`, the meta description, the `areaServed` list, the `GeoCircle`, the service-area
   block and the footer. If the business is actually in Missouri, all of those change.
2. **The Yelp review.** I could not open Yelp — it returns 403 to curl, to a crawler
   user-agent, to a mobile UA and to a reader proxy, for real and invented slugs alike. The
   quote on the page (*"Damaris and Naileth did an amazing job. Extremely thorough, kind."*)
   is assembled from search-result snippets that two independent searches agreed on. Get the
   **verbatim text, the reviewer's name and the direct listing URL** from the client. The
   "Read it on Yelp" link currently points at a Yelp *search* for the business, because a
   business URL I cannot verify is worse than a search that always resolves.
3. **"About ten minutes."** The response time in the checks list comes from the Yelp listing
   as reported in the brief, not from anything I could read myself. Confirm or drop the line.
4. **Service one-liners.** Their site describes only three services in prose (Health Reset,
   Move In / Move Out, Routine & Maintenance). The other four descriptions are mine, written
   to stay inside what their copy already claims. Have the client rewrite them in their own
   words; these are the lines most likely to be subtly wrong.
5. **Trade names.** *Virex Tb* appears in a photograph and in that photo's `alt`. Fine as a
   description of what is in the frame; check they are happy naming the product.
6. **Founding year.** Not confirmed anywhere, so the page never claims one. If they have it,
   it is worth adding — "since YYYY" is a real trust signal.

## 2. What was cut, and why

- **The kitchen photograph is not on the page.** It is the only wide "beauty" shot they own,
  and I dropped it: the file is 1279×771 with six rows of pure black at the bottom, which is
  a letterbox left by cropping something else, and the filename is SEO copy rather than a
  camera name. Origin unconfirmed, so it does not go on a page whose whole argument is
  "these are our own jobs". If the client shot it, put it back; if they need a hero-width
  photo, that is the single most valuable thing they could send.
- **No star badge.** They have exactly one review. The page says so in words instead:
  *"Five stars, and exactly one review. We are not going to dress that up."*
- **No `aggregateRating` in the schema.** A 5.0 from one review invites a manual penalty and
  looks worse in a rich result than no rating at all.
- **No prices.** Their funnel is deliberately walkthrough-first, so the page argues for the
  walkthrough instead of inventing a "starting at $X".
- **Their typos are not carried over:** `the air you breath` → breathe, `health-conscience`
  → health-conscious, `Reoccurring` → Recurring, `detail, That's why` → sentence break. The
  microbe list (where `listeria` and `monocytogenes` are split into two organisms) and the
  dust-mite statistics are not reproduced at all — unsourced health numbers, and the page
  does not need them.
- **The old favicon is not reused.** The file at their favicon URL is the logo of
  **FOCK CLEANING — A HIGHER STANDARD OF CLEAN**, a different company. Right now a browser
  tab open on lux360clean.com displays a competitor's mark.

## 3. Where the photographs came from

All eleven images are the client's own, pulled from their Squarespace CDN at `?format=2000w`.

The five before/after pictures needed work. They arrived as **stitched diptychs**: two
photographs side by side in one 760×500 file, with `BEFORE` and `AFTER` burned into a bar
across the top. Used whole in a drag control they produce garbage — at the halfway point the
two words overlap and read `BEFER`. So each file was split at the gutter, the caption bar and
the stitching frame were cropped off, and both halves were normalised to a single 4:5 crop at
560×700. The labels on the page are now HTML, positioned per layer, and each fades out as its
side of the frame closes.

Two consequences worth knowing:

- **Resolution is the ceiling on this section.** Each half starts life about 368 px wide, so
  the largest honest display size is around 490 px. Blown up further they go soft. The
  original camera files would let this block run full-bleed.
- **The pairs are hand-held, not tripod-matched.** Framing shifts between before and after
  (the oven has its racks in on one side and out on the other), so the wipe reads as two
  photographs of the same subject rather than one frame changing. That is why each layer
  carries its own `BEFORE` / `AFTER` label: the control never pretends the two frames are
  pixel-aligned.

Filename → what it actually shows, because the client's names are misleading:

| Client's file | On this page | Subject |
|---|---|---|
| `Shower Before and After` | `*-grout` | shower floor, tile and grout |
| `Streak Free Mirror Before and After` | `*-glass` | shower glass, not a mirror |
| `Window Sill Before and After` | `*-sill` | window sill and frame corner |
| `Oven Before and After` | `*-oven` | oven door and cavity |
| `Lux360 Clean Baseboard Before & After` | `*-baseboard` | baseboard and floor edge |

## 4. Design decisions

**Direction.** Clinical daylight: a nurse's chart crossed with a bright Hill Country house at
ten in the morning. Dyson's habit of explaining what you cannot see, Aesop's air, Oura's one
warm metal in a calm layout. Explicitly not the cleaning-category visual language — no yellow
gloves, no blue-green gradient, no three icons labelled Residential / Commercial / Move-out.

**Gold is light, not metal.** Their logo is a gold gradient on black, and carried literally
into an interface that reads as limousine service, which is the wrong signal for people who
are letting strangers into a house with children in it. Their own slogan gives the way out:
*Let the Light In*. So the page is light, and the gold appears as a warm bloom on the hero
photograph, one hairline, the protocol dial, the drag handle and a single dark band. There is
no gradient on gold anywhere in the interface and no sparkle used as decoration.

**Type.** One family, Libre Franklin. The logo is a Didone, and extending high-contrast serif
into the page would land in wedding-salon territory; keeping the page in an American gothic
means the logo stays the only high-contrast thing on screen, which is where the tension should
be. Four sizes and no more.

**The signature detail.** The broken circle in their logo becomes the protocol dial: one
circle cut into three arcs, one per step of their method, drawn in order as the section
arrives. It makes *360* mean something structural rather than decorative, and it ties to a
real claim — dwell time is a duration, and a duration is an arc.

**The one dark band.** The page is light and locked light, with a single exception: the band
carrying *"It's not about shine. It's about reducing microbial load."* is their logo's black
and gold. One theme switch, used once, where the brand signs its name.

**Deliberately not done:** no carousel, no parallax, no odometer counters, no glassmorphism,
no three-identical-cards row, no stock photography, no `#007BFF`, no em dashes in copy that
is ours (verbatim quotes from the client keep their own punctuation).

**Departure from the brief's hero frame.** The brief specifies a full-viewport photograph with
a scrim. With the kitchen shot dropped, the only remaining hero-capable image is the
disinfectant photograph, which is portrait and detail-scale and dies stretched to `92vh`. So
the hero is an asymmetric split instead: copy on the shell grid, photograph bleeding off the
right edge at a size it can actually hold. The headline sits on clean ground, which also makes
its contrast trivially safe rather than scrim-dependent.

## 5. The before/after control

`clip-path: inset()` on a single after layer, driven by a spring rather than a CSS transition,
because a transition cannot be grabbed and reversed mid-flight.

- Pointer Events with `setPointerCapture`, so the drag survives the pointer leaving the frame.
- The grab offset is preserved: taking hold of the handle 15 px off centre does not snap the
  line to the finger. Pressing on the photograph instead moves the line to that point.
- 6 px of hysteresis before a press commits to a drag.
- Release hands the pointer's velocity to the spring, and the landing point comes from Apple's
  exponential projection (`(v/1000)·d/(1−d)`), not `v²/2a`. Deceleration is 0.99 rather than
  the scroll-like 0.998 and the projection is capped at 20 %: this control exists to *place*
  a line, so a flick should glide, not fling to an end.
- Rubber-banding past either end during the drag, bounded to 4 %, and the frame does not clip
  the knob, so the resistance is actually visible instead of theoretical. Below 460 px the
  page gutter is too narrow for the overhang and the frame clips again; that is a touch
  width, where the resistance is felt in the finger anyway.
- On release the spring settles critically damped with no velocity handoff when it lands on
  an end, so the divider never sails outside the frame.
- Release velocity is ignored if the newest pointer sample is more than 90 ms old. No
  `pointermove` fires while a finger rests, so without that check a drag-then-hold released
  a second later would fling as if it were still moving.
- A press decides nothing. The stage allows vertical panning, so a finger landing on a
  photograph may be the start of a scroll; the position is committed on `pointerup` and not
  at all on `pointercancel`. A second pointer cannot take over a drag in progress.
- Keyboard: `role="slider"` on a real `<button>`. Arrows ±2, Shift+arrows ±10, PageUp/Down
  ±10, Home/End. `aria-valuetext` is spelled out in words.
- `prefers-reduced-motion` drops the control entirely and shows the two photographs side by
  side, which restores the client's original diptych. The instruction line swaps too, so the
  page never tells a reduced-motion visitor to drag a handle that is not there.
- The first control on the page moves itself once, 50 → 63 → 50, when it first scrolls into
  view. That is the only way the affordance is taught without a label. It runs through the
  same spring the gesture does, so a press interrupts it; and once anyone has touched or
  typed at the control, the return leg is abandoned rather than overruling a position the
  visitor chose. The nudge commits its value as it goes, so `aria-valuenow` and the arrow
  keys stay in step with what is on screen.

## 6. Motion

Baseline is fade plus 8 px rise, 500 ms on `cubic-bezier(.2,.7,.2,1)`, 60 ms stagger inside a
group. Only four things animate: sections arriving, the header thickening, press feedback on
buttons, and the drag control.

**Rejected, on purpose:** a hero entrance sequence (an element starting at `opacity: 0` is not
counted as rendered, so it would push LCP for the sake of decoration); hover lift on the
before/after frames (they are not cards and not clickable as a whole); a marquee of service
names; parallax on the hero photograph; any transition on focus rings, which must be instant.

The reveal is wired first and everything after it is inside `try/catch`. A 2.5 s timer and a
`window.onerror` hook both force every section visible, so a script error cannot leave half the
page invisible. The timer is cleared the moment the observer is actually watching — left armed
it fires mid-read and reveals the whole page at once, which is exactly the bug the code review
caught.

## 7. Against the current Squarespace site

Measured on 15 Sep 2026.

| | lux360clean.com | this page |
|---|---|---|
| HTML document | 411 KB | 54 KB (16 KB gzipped with the CSS) |
| JS + CSS files | **45 files, 5.9 MB** uncompressed | **0** |
| Requests before first paint | 46+ | 4 |
| First view over the wire | ~360 KB before a single photograph | ~202 KB including the hero photograph |
| Third-party origins loaded | 5 (Squarespace, two CDNs, CloudFront, a form embed) | 0 |
| Favicon | a competitor's logo, **FOCK CLEANING** | their own logomark |
| Geography | "Osage Beach, Lake Ozark" on a 512 number | Austin and named western suburbs |
| Phone in the first screen | no | yes, and a sticky tap-to-call bar under 1060 px |
| Reviews page | empty, `<title>` still reads "Team 1" | the one real review, quoted, with the count stated |
| Before/after | five static images | five drag controls, with keyboard and a reduced-motion fallback |
| Structured data | none | `CleaningService` with `areaServed`, `GeoCircle`, `founder`, seven-item `hasOfferCatalog` |
| Social card | none | `og.jpg`, 1200×630 |

The JS figure is the one to quote. 5.9 MB of script and stylesheet across 45 files still has to
be fetched, decompressed, parsed and executed on a phone on suburban LTE, and none of it does
anything this page needs.

## 8. Checks run

- No horizontal scroll at 320, 360, 390, 768, 960, 1060, 1440 and 1920 px — `scrollWidth`
  compared against `clientWidth`, not judged by eye. Two real overflows were found this way
  and fixed: a fixed 320 px cap on the portrait at 320 px viewport, and the header's nav
  colliding with its button at 960 px.
- Contrast measured in both directions: ink on ground 16.3:1, muted 6.1:1, accent text on
  light 5.7:1, white on the caption chips 13.8:1, gold-light on black 15.2:1, black on the
  gold button 10.9:1. The focus ring is ink on light and gold-light on the dark bands, so it
  never matches what it sits on.
- The drag control driven with real pointer, touch and key events: 1:1 tracking verified
  against predicted values, grab offset preserved, clamping at both ends, tap-to-position,
  interruption mid-flight, a second finger unable to hijack an active drag, a touch that
  becomes a vertical scroll leaving the divider alone, and drag-then-hold releasing without
  momentum while drag-then-flick keeps it.
- Progressive scroll reveals all 27 animated blocks; a deep link to `#services` lands 88 px
  down, clearing the 68 px sticky header.
- A full code review of `index.html`, which found ten defects. All ten were fixed. The one
  that mattered: the 2.5 s "nothing stays invisible" failsafe was never cancelled once the
  IntersectionObserver was wired, so two and a half seconds after load the entire page
  revealed itself at once and the scroll animation effectively never ran. The rest were in
  the drag control and are described in section 5. Two were latent layout bugs the width
  sweep had missed because it skipped the 420–520 px band: the header phone button collided
  with the wordmark there, and the knob, once unclipped, pushed the document 2 px wide on
  phones.
- Reviewed against the Web Interface Guidelines. Fixed: straight apostrophes throughout,
  missing `scroll-margin-top` under the sticky header, no `text-wrap: balance` on headings,
  missing `touch-action: manipulation`, unset tap-highlight colour, no `color-scheme`, and no
  safe-area insets on the full-bleed edges. **Rejected** two of its rules: Title Case for
  headings, and avoiding first person. Sentence case is the editorial voice here, and a
  company describing itself as "we" is correct for this page.

Not run, because they refuse model invocation and need to be started by hand:
`/hallmark`, `/prototype`, `/review-animations`.

## 9. Still to do

- `sitemap.xml` — `robots.txt` already references it.
- Analytics, if they want any. Nothing is currently loaded, which is why the third-party
  count is zero. The only outside URLs in the file are the `schema.org` context string, which
  is an identifier and never fetched, and the Yelp link, which is a link a visitor clicks.
- Terms of Service and Privacy Policy. The current site has both; this page does not link
  them, since the URLs will change with the platform.
