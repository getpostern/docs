# The Postern docs page template

**This is a specification, not advice. Build against it literally.**

Every page in this repo has the same skeleton, in the same order, using the same
components. Where a page needs something this document does not authorise, the
answer is no — raise it as an open question at the bottom of your ledger instead
of inventing a shape.

## Precedence

1. **The founder's voice ruling** (the plain-English brief). It overrides
   everything below, including the house style guide.
2. **This template.** It is the Mintlify-specific finalisation of house style §2.
   Where the two differ, this document wins and §0 of this file records why.
3. **`docs/reference/docs-house-style.md`** — R1–R34, the no-loss protocol (§3),
   the ledger, the six gates. All still binding. This template does not repeal a
   single rule; it decides how each one is expressed in MDX.
4. **`soul.md`** — the register only: careful, precise, no marketing, no
   exclamation marks, and the honesty regime (every claim traceable to code,
   future work labelled as future, no number without published methodology).
   **The apparatus does not survive.** house-style R29 ("the jacket is
   constitutional") governs `site/guides/`, which is still live and unchanged.
   It does not govern this repo.

## The one constraint everything serves

> Make the onboarding as simple and straightforward as possible **while ensuring
> there is no loss of information.**

The only legal deletion is redundancy — text restating what is already legibly on
the reader's screen or already stated on the same page. Everything else moves, and
every move gets a ledger row (§9). **A page ships when its ledger reaches zero
orphans, not when it gets shorter.**

---

# §0 · The eight rulings

These are the decisions this document was written to make. Each is final.

## Ruling 1 — Nothing replaces the kicker

`FIELD GUIDE · RAISING YOUR GATE · № 01 · THE GATE` is deleted and **no element
takes its place.** There is no eyebrow, no strip, no bolded lead line, no italic
banner between the H1 and the first content. That slot belongs to the frontmatter
`description` and to nothing else.

The kicker did four jobs. Three of them have homes; one was redundant on arrival:

| Segment | Disposition | Where it goes |
|---|---|---|
| `FIELD GUIDE` | `DELETED-REDUNDANT` | Costume. The reader knows they are in documentation because they are on a documentation site. |
| `RAISING YOUR GATE` / `CONNECTING A SOURCE` / `REACHING YOUR GATE` | `MOVED` | The **navigation group name** in `docs.json` (§7). The taxonomy survives in full; it moves from a banner nobody reads to a sidebar every reader uses. |
| `№ 01` | `DELETED-REDUNDANT` | Sidebar position carries it, and the sidebar stays true when pages are inserted. A hard-coded ordinal does not. |
| `THE GATE` | `DELETED-REDUNDANT` | Says the same thing as the H1 two words later. Bucket A, case 3 (same fact twice on one page). |

**Reasoning.** Every framework in the research pass says the same thing about
pre-title matter: readers do not read it. Carroll & Rosson's production bias
("learners at every level of experience try to avoid reading"), Meng/Steinhardt/
Schubert's opportunistic developers who jump straight to the snippet, and NN/g's
layer-cake scanning all predict that a four-part all-caps banner is scanned past
on the way to the first heading. It cost seven words of vertical space above the
fold and delivered one fact (the taxonomy) that the sidebar delivers better and
keeps true automatically.

**The `meta` triple is not part of the kicker and does not die with it.**
`docker + a terminal · about ten minutes · no cloud account, because there is no
cloud` is the honest price and it is load-bearing for a reader deciding whether
to start. It becomes the **first three bullets of the Before-you-start block**
(§5.1). It never floats as an italic line under the title.

## Ruling 2 — The specimen illustration does not appear. Anywhere.

**No botanical drawing, no drawn gate mark, no inline `<svg>` in the body of any
page in this repo.** Not in the title area, not in the margin, not at any size.

The brief contains a contradiction: its structural section says the specimen
survives as brand; its voice section — which states outright that it "overrides
EVERYTHING else you read" — bans decorative illustrations and says drawings
belong on the website. **The voice section governs.** It is later, it claims
override authority explicitly, and it is the founder's own words rather than a
gloss on them.

The practical case is the same one. A drawing above the H1 is a preamble with a
picture in it — the same slot, the same scan-past, and on a page someone opened
because they cannot reach port 8787 it reads as decoration in front of the
answer. Screenshots stay, without exception, because a screenshot is instruction.

**Brand still carries, through the surfaces that are chrome rather than page
content**, all already declared and requiring no page-level markup:

- the three faces — Cormorant Garamond, EB Garamond, Courier Prime (`docs.json`
  `fonts`, `style.css`);
- the paper and ink — `#F5EDDA` / `#151F19` backgrounds, `#E7A42A` poppy primary
  (`docs.json` `colors`, `background`);
- `favicon.svg` and the navbar mark.

`images/specimen-*.svg` are unused in this repo. Leave them on disk; do not
reference them. Delete the `<svg>` currently sitting at `start/install.mdx:6`.

## Ruling 3 — Section order is fixed, and it puts recovery next to verification

Both page kinds run the same order. The one place this template **overrides house
style §2** is the position of the troubleshooting index:

> house style §2: `check` → `stands` → `IF IT STILL WON'T`
> **this template: Confirm it works → If something went wrong → What you have now**

**Why.** The reader who fails the confirm needs the recovery in the next screen,
not two sections away. The contiguity principle is the largest effect in the 2025
meta-analysis (g ≈ 0.74) and it is a *placement* effect, not a length effect; van
der Meij & Carroll's 2021 revision splits heuristic 3.4 from 3.6 — "is error
information offered" from "is it near the procedure" — precisely because teams
satisfy the first and fail the second. Putting a postconditions section between a
failed check and its recovery is that failure in miniature. The reader who
*passes* the confirm pays one heading of scroll, and a heading is skippable at a
glance.

## Ruling 4 — Prerequisites are stated three times, on purpose

Production bias is unambiguous: the reader jumps to the first code fence. So a
prerequisite is never stated once.

1. **In the `<Info>` block**, which is the first thing on the page and is a
   coloured box — it survives a scan that skips prose.
2. **Again at the step where it bites**, in the step body, verbatim if that is
   clearest. This is house-style R6 and it is the one that actually works,
   because the box gets skipped and the step does not.
3. **Never above the first code fence and nowhere else.** If a fact gates a
   command, it appears in the same `<Step>` as that command. No exceptions.

**Hard rule: no code fence may appear above the `<Info>` block.** It is
mechanically checkable and it is what stops the block being scrolled past.

The word count of a correct page goes **up** here. That is the expected
direction.

## Ruling 5 — A step's success is confirmed in the same paragraph, in prose

Three tiers, and only the third is a component.

- **Step result — mandatory on every state-changing step.** The last sentence of
  the step's action paragraph, present tense, observable. *"The Google card turns
  to Connected and two connections appear beneath it."* Google's rule: state the
  action first and the result second, and keep the result **in the same
  paragraph as the action**. It is prose. It is not a box.
- **Command checkpoint — mandatory where success is not visible in a UI.** A
  second fenced block in the same step, showing the command and its literal
  expected output, introduced by a sentence that states the expected value in
  words as well. Never asserted without a witnessed run (gate G5).
- **Page checkpoint** — the `## Confirm it works` section (§5.6).

Why no component per step: eight green boxes on a page is texture, and texture
destroys the signal of the two boxes that matter. The callout budget belongs to
failure, not to success.

## Ruling 6 — Traps are set at the act, and the direction depends on reversibility

- A warning about an **irreversible act** goes **immediately before** the
  instruction that performs it. The reader must know the key shows once *before*
  the click that mints it, and that `docker compose down -v` is unrecoverable
  *before* they meet the command.
- A warning about a **failure you will hit** goes **immediately after** the
  action that triggers it, inside the same `<Step>`.
- **Never** as a preamble at the top of the page. **Never** with its only home in
  a troubleshooting section. **Never** inside anything collapsible — there is
  nothing collapsible in this repo (§6).

Two tiers, two components, matching the site's own TRAP/SNAG distinction:

| Tier | Component | For | Budget |
|---|---|---|---|
| Trap | `<Warning>` | The irreversible, and the silent failure that costs an afternoon | **0–3 per page.** Never two consecutively. |
| Snag | `<Note>` | The recoverable: what you will see, why, what to do | Ranked, not unlimited. If a page needs more than about five, split the page. |

A `<Warning>` whose remedy is "try again" is misfiled — it is a `<Note>`. That
rarity is the entire mechanism.

**Shape inside the callout**, three moves in this order, no labels (the component
already carries an icon; `**TRAP** ·` inside a `<Warning>` is the costume
sneaking back in):

1. **What you see** — symptom first, because that is what a stuck reader is
   scanning for. Any literal third-party string goes in backticks so it is
   greppable: `` `redirect_uri_mismatch` ``.
2. **Why** — the mechanism, one clause.
3. **What to do** — the instruction.

**Every quoted string must be witnessed** (R17, gate G5). If nobody has seen it,
write the entry symptom-first and quote nothing: *"the container exits within
seconds"*, never an invented error message. A near-miss string makes the reader
trust the page less, not more.

## Ruling 7 — The page ends with one `## Next` section and nothing after it

No back-link, no horizontal rule, no `← all sources · next guide →` foot line.
Mintlify already renders previous/next page links from the navigation order; a
hand-written foot line is duplicate furniture (`DELETED-REDUNDANT`, evidence:
the auto footer).

`## Next` is the last thing on every page:

- **Spine page** → exactly **one** `<Card>`, the next spine page. The spine is a
  sequence.
- **Connector page and the last spine page** → a `<Columns cols={2}>` of cards,
  an *or* group. Each card body quotes that destination's own cost line
  (*"a Bridge subscription (~$1.50/mo, paid by you) · about five minutes · paste
  one token"*). Never a marketing-style comparison table; that register does not
  exist here.

This is house-style R4 made mechanical: one journey, with the connectors hanging
off it as an *or*, and the forward link a suggestion rather than an ordinal.

## Ruling 8 — The component roster is closed

See §6 for the full list with reasons. The headline: **no Accordion, no Tabs, no
Expandable, no `<Visibility for="humans">`, no `<Tip>`, no `<Check>`, no
`<Danger>`, no Mermaid, no emoji.** Nothing on a Postern docs page hides content
from a human reader. Relocation is a sibling H2 or a sibling page — never a
collapse.

---

# §1 · Frontmatter

Two fields. Exactly two.

```yaml
---
title: "Connect Google and Gmail"
description: "Calendar and contacts through your own Google Cloud app; Gmail separately over IMAP."
---
```

**`title`**

- The reader's goal, not the machinery. *"Connect Google and Gmail"*, never
  *"Google OAuth configuration"* (R8).
- Renders as the H1 **and** as the sidebar label. Keep it short enough to serve
  both — six words is a ceiling, four is better.
- No numbering. No `№`. No "Guide". No colon-and-subtitle construction.
- **Never write `# ` in the body.** The H1 comes from here and there is exactly
  one per page.

**`description`**

- One sentence: what will be true when the reader finishes, plus the one shape
  fact that decides whether this page is for them.
- **≤ 160 characters.** It is both the page subtitle under the H1 and the meta
  description; over 160 it truncates in search and reads as a paragraph on page.
- Never a benefit sentence. Never a congratulation. **Never a number without a
  `product-truth.md` row** — the current `start/install.mdx` description carries
  *"measured cold, healthy in about twenty seconds"*, which has none and is
  blocked on house-style §6 · R-2.

Nothing else goes in frontmatter. No `sidebarTitle`, no `icon`, no `mode`, no
`tag`.

---

# §2 · Connector page — the skeleton

Copy this shape literally. Sections in this order; omit only where marked
optional.

````mdx
---
title: "Connect <source>"
description: "<one sentence: what is true at the end>"
---

<Info>
  **Before you start**

  - **<what you must already have>** — <the account, subscription, or device>
  - **About <n> minutes.**
  - **<the shape of the credential>** — <app password / OAuth client / token>
  - **<any prerequisite that gates a step later>** — <stated flatly>
  - **<a one-time secret appears in this session>** — open your password manager
    first.
</Info>

## Choose your path                      <!-- optional; only if the page branches -->

<one sentence naming the split>

| If… | Then |
|---|---|
| <condition, stated first> | <destination, always a link or an anchor> |

<Steps>

<Step title="<imperative + consequence>" titleSize="h2" id="<stable-slug>">

<Location first, action second, result in the same paragraph.>

```bash
<the exact string, complete, copy-pasteable>
```

<Frame caption="<the discriminator, visibly>">
  <img src="/images/<file>.png" alt="<the fact the shot carries>" />
</Frame>

<Note>
  <symptom> — <mechanism> — <what to do>
</Note>

</Step>

<!-- more steps -->

</Steps>

## Confirm it works

<one sentence: what this proves>

- <observable state, and what it must read>
- <…3–7 items, killer items only>

## If something went wrong

| What you see | Where it is answered |
|---|---|
| `<literal string>` | [<step title>](#<step-id>) |
| <named symptom> | [<step title>](#<step-id>) |

## What you have now

<what exists · what an agent can now do · the standing cost the reader has just
taken on.>

## Next

<Columns cols={2}>
  <Card title="<destination>" href="/<path>">
    <that page's own cost line, quoted>
  </Card>
</Columns>
````

---

# §3 · Spine page — the skeleton and what differs

Same order, same components, four differences:

1. **No fork table**, except where a genuine environment split exists and both
   arms are supported. R2: the first run has no forks. A spine page must work for
   every reader every time. Variants leave as a link in `## Next` or as a named
   late H2 on the same page (*"If your gate is on Postern < 0.x"*), never as an
   inline conditional inside a step sentence.
   **The one authorised exception is `start/open-the-console`**, whose entire
   subject is a two-arm split (§7.2).
2. **`## Next` carries exactly one card** — the next spine page — except on
   `start/connect-an-agent`, which is the seam where the spine becomes an *or*
   group and therefore ships the connector `<Columns>`.
3. **`## If something went wrong` is mandatory**, not optional. A spine page is
   where a first-timer is stuck with no support channel.
4. **Every fact a later page will need is owned here, once.** §7 says exactly
   what each page owns and what it must not restate.

---

# §4 · The step

```mdx
<Step title="Create the app password, paste it with your address" titleSize="h2" id="app-password">
```

**`titleSize="h2"` is mandatory on every step.** This is the ruling that makes
R14 work in Mintlify: an `h2` step title becomes a real heading, which becomes a
real anchor, which is what the `## If something went wrong` index links to and
what a support reply can name by URL. Do not put a wrapping H2 above `<Steps>` —
the steps *are* the page's top-level sections, and the resulting table of
contents reads exactly like the procedure.

**`id` is mandatory**, kebab-case, stable, named for the act:
`app-password`, `enable-apis`, `consent-screen`, `oauth-client`, `scopes`,
`publish`. Never `step-3` — step numbers renumber, ids must not.

**Step numbering is permitted and expected.** Mintlify draws a number in the
gutter of each `<Step>`. That is standard procedure UI in every serious docs site
and is not what the ban on numbering meant: the ban is on numbering *pages*
(`№ 01`), which is website apparatus the nav replaces.

**Title:** imperative verb first, naming the consequence.
*"Clone, seed a password, start the stack"* — correct.
*"Installation"* — a category, not a title.

**Body, in this order:**

| Slot | Form | Carries | Never |
|---|---|---|---|
| action | paragraph | Location first, one action, result in the same paragraph | narration of a screenshot |
| value | fenced block | the exact string, complete, copy-pasteable | `<placeholder>` where the Console hands over a real value |
| evidence | `<Frame caption>` + `img alt` | the screen at legible scale | a shot the prose then reads aloud |
| trap | `<Warning>` **before** the act | the irreversible only | ordinary friction |
| snag | `<Note>` **after** the act | the recoverable failure | anything unwitnessed |

**Location first, action second** (R9). *"Console → Sources → Google → paste the
client ID"*, not *"Paste the client ID (in the Console)"*. This is the
highest-leverage no-loss rule in the set: it makes an irrelevant step skippable
at a glance **instead of deleted**, and it costs zero words.

**One action per step.** Past about nine discrete imperatives, split the step.

**Never in a step:** an explanation longer than one clause; a second procedure; a
choice. A choice is a fork and forks live in the fork table.

**Do not chop causal joins into imperatives.** Some sentences carry their
information in their structure:

> *"A 403 on calendar or contacts right after a successful sign-in means the APIs
> are not enabled in the project that owns your client — the most common
> post-consent failure, and the error will not say so."*

Broken into three short imperatives, the em-dash causal join — which **is** the
information — is gone. Read every restructured step aloud against the source
before you commit it.

---

# §5 · Every element, specified

## 5.1 · `<Info>` — Before you start

**Exactly one per page. Always the first thing after the frontmatter. Never used
for anything else, ever.** One component, one job, so a returning reader
recognises the block by shape before reading a word of it.

Contents, in this order — a bulleted list with a **bold lead noun** on each row,
never a paragraph:

1. The cost triple, inherited from the guide's `meta` line: what you must already
   have · how long · the shape of the credential.
2. The machine and shell assumption, stated flatly.
3. What must exist elsewhere first — an account, a running service, a
   subscription and its cost, an admin role, a device physically in hand, 2FA
   already on.
4. What the first run consumes — a pull, a fee, a one-time token.
5. What ports or addresses get taken, and on which interface.
6. Any approval lead time measured in **calendar** days.
7. What obligation the reader is accepting — patching, uptime, cost.
8. Whether a one-time secret will be shown during this session — i.e. *open your
   password manager first*.

**Never:** architecture. Never the security model as education. Never a fact that
appears *only* here (Ruling 4). Never empty — three of the eleven live guides
ship an empty prerequisite slot, which trains a reader who scans for the block to
conclude there are no prerequisites.

Heading inside the callout is `**Before you start**` in bold, not an H2 — the
callout is not a document section and must not appear in the table of contents.

## 5.2 · `## Choose your path` — the fork

A two-column Markdown table. Present **only** when the page genuinely branches;
absent otherwise.

- Column 1 is the **condition**, stated first, in the reader's own terms
  (*"your gate runs on this machine"*, *"a Google Workspace account"*, *"the
  reveal screen shows a ready-made config"*).
- Column 2 is the destination, **always** a link or an on-page anchor.
- About six rows is the ceiling.
- **A branch that lives in a fork table must not also survive as a parenthetical
  inside a step** (R12). A parenthetical beginning "(if you…)" inside a step body
  fails review.

Surfacing a branch usually *reveals* facts the prose was burying. This rule adds
information more often than it moves it.

## 5.3 · Code

- **Every fence carries a language tag.** `bash`, `json`, `text`, `yaml`.
- **No `$` prompt prefix.** It breaks copy-paste, which is the whole point.
- One command per line. Multi-line continuations keep their backslashes.
- **Expected output is its own fence**, immediately under, introduced by a
  sentence that states the expected value in words too. A comment inside the
  command fence is invisible to a scanning reader.
- **Exception, and it is the existing witnessed form:** a verification command
  whose expected status code *is* the fact may carry it as a trailing shell
  comment (`# MUST be 404 — a 200 means the admin surface is exposed: STOP`),
  because the comment is shell-legal, survives paste, and is what the reader runs
  against. When it does, **the same expected value must also appear in the
  introducing sentence.** Costs one clause, loses nothing.
- **Placeholders fail loudly, in two forms:**
  - `<lowercase-hyphen>` for hosts, ids and names — `<your-box>`,
    `<connection-id>`. Pasted verbatim, it already fails at DNS or lookup.
  - `UPPER_SNAKE` for secrets and credentials — `YOUR_CLIENT_SECRET`.
    Pasted verbatim, the command must break rather than half-work.
- **Never a real secret, token, password, hostname, account, or connection id.**
  Example tailnet names use `example-tailnet.ts.net`, which is the site's own
  convention.
- **Where the Console hands over a ready-made artefact, lead with copying it**,
  not with retyping into it (R24). Hand-substituting a key into a CLI line is
  more work than needed, covers one harness only, and writes a live credential
  into the reader's shell history.
- **Drifting values** — ports, redirect URIs, image tags, volume names — are
  printed inline, in full, at the step (R21 beats Diátaxis on placement). They
  are kept true by generation from one constants map, never by a link. **No step
  may say "see the reference for the exact value."**

## 5.4 · Images

```mdx
<Frame caption="Continue is the small link on the left, not the blue button.">
  <img src="/images/google-unverified.png" alt="Google's unverified-app interstitial: a prominent blue Back to safety button, with Continue as a small link beneath it." />
</Frame>
```

- **`alt` carries the fact.** It is for screen-reader and images-off readers;
  sighted readers never receive it.
- **`caption` carries the discriminator visibly.** Where the alt names the thing
  that decides the step — *"Continue is the small link, not the blue button"* —
  those words must also exist as a caption. Two structurally identical image rows
  where one has a caption and one does not is a live defect on the current site.
- **The legibility gate (R25).** Mintlify's content column renders at roughly
  **720px**. Compute `720 ÷ native_width`. If the smallest text the fact depends
  on lands below ~11px rendered, the shot is not that fact's home: **crop it, and
  rename the file**, before citing it as a relocation target. A 1440-wide native
  capture renders at 50%, so any fact set below ~22px native is illegible.
  `gate-mint-key.png` (1440×900), `google-scopes.png` (1020×700) and
  `google-audience.png` (1500×840) all fail today.
- **A value never lives only in an image.** If the shot is the only copy of a
  string, the string is also written as text.
- **New filename on any content change.** In-place replacement leaves browsers
  serving the old bytes. `apple-health-card.png` → `apple-health-endpoint.png` is
  the precedent.
- **Dead names, never use:** `google-console-gmail.png` (leaked a live
  credential; the redacted replacement is `google-console-gmail-redacted.png`),
  `apple-health-card.png`.
- **No browser chrome, no personal data, no live credentials, no real account
  addresses.**
- Images live at `/images/<filename>`.

## 5.5 · `<Warning>` and `<Note>`

Specified in full in Ruling 6. The additional mechanical requirements:

- Each callout sits inside the `<Step>` it belongs to, never between steps.
- Never two `<Warning>` consecutively, and never more than one per step.
- Never nested inside any other component.
- The `## If something went wrong` index links to the **step anchor** that owns
  the callout, not to the callout itself — step anchors are guaranteed by
  `titleSize="h2"`; callout anchors are not.

## 5.6 · `## Confirm it works`

The page's do-confirm pause point.

- **3 to 7 items. Killer items only** — the steps most dangerous to skip and most
  often skipped. Not a restatement of the procedure.
- **Observable state only:** a status code, a non-empty result, a future expiry
  date, a card reading Connected, a row appearing in the ledger.
- Rendered as a Markdown bullet list. Where commands exist, one fenced block
  carrying them, per §5.3.
- **No expected value that has not been run.** A confirm section that publishes a
  MUST which fails for correct installs is worse than no confirm section. Gate
  G5.
- **Match the register to the page.** Do not clone the remote-access curls onto a
  connector page: those carry MUST semantics and a STOP because a wrong state
  there is a live security exposure. A connector's failure mode is "no
  transactions yet". Uniform verification furniture flattens a distinction the
  set encodes on purpose.
- `## What you have now` may assert nothing this section cannot demonstrate.

## 5.7 · `## If something went wrong`

A two-column table: **What you see** → **Where it is answered**.

- Indexes **both** literal error strings and named symptoms or hazards. An
  error-strings-only index silently drops about a quarter of the real traps —
  the Mac PATH trap (`which tailscale` returns nothing), the Let's Encrypt
  issuance-limit trap, the password-manager-covers-the-button trap, the
  exported-JSON-contains-your-live-secret trap. Those are symptom-shaped, not
  message-shaped.
- Every row links to a step anchor on this page. **One home, one pointer.**
- It also carries the cross-cutting failures that belong to no single step: clock
  skew, the container cannot reach the host, a reverse proxy in front.
- **It is never the only place a failure is described.** It is an index. The
  description lives at the step.

## 5.8 · `## What you have now`

- **Carries:** what now exists; what an agent can now do; **and the standing cost
  the reader has just taken on** — the weekly re-consent, the annual bank reauth,
  the subscription, the patching, the revocation semantics.
- Postconditions phrased as consequences are the register and are correct:
  *"disconnecting revokes only the sealed access"*, *"revoke at Apple and the
  gate goes quiet"*, *"`/item/remove` also stops the billing"*.
- **Never a congratulation.** Never an outcome `## Confirm it works` cannot
  demonstrate.
- **Never a smuggled step.** Where a procedure genuinely belongs here, extract it
  to its own step or its own page — and when you extract, **all** of it moves,
  including trailing clauses. The remote-access teardown is three elements
  (`funnel --https=443 off`, clearing the address in Settings, **and a restart**);
  a mechanical command-extraction drops the third and leaves the reader with a
  bridge advertising a dead origin.

**Heading wording note.** The founder's approved phrase is *"What you will have
when you are done"*. This section sits at the **end** of the page, after the work,
so it is written in the present: **`## What you have now`**. Same substance, right
tense for its position. Flagged in §11 for confirmation.

## 5.9 · `## Next`

Specified in Ruling 7. Card bodies quote the destination's own cost line; they do
not invent new copy.

---

# §6 · The component roster

## Approved

| Component | Use | Constraint |
|---|---|---|
| `<Info>` | Before you start | **Exactly one per page**, always first, never used for anything else |
| `<Warning>` | Trap tier — irreversible acts, silent afternoon-costing failures | 0–3 per page; never consecutive; never nested |
| `<Note>` | Snag tier — recoverable failures | Ranked; if a page needs > ~5, split the page |
| `<Steps>` / `<Step>` | The procedure | Every step: `title`, `titleSize="h2"`, `id` |
| `<Frame>` + `<img>` | Screenshots | `caption` on the Frame, `alt` on the img, §5.4 legibility gate |
| Fenced code blocks | Every literal string | Language tag mandatory; no `$` prefix |
| Markdown tables | The fork; the troubleshooting index | Condition in column 1 |
| `<Card>` / `<Columns>` | `## Next` only | Legacy name `<CardGroup>` still renders; pick one and keep it |
| `<Visibility for="agents">` | Additive agent-only detail — e.g. the exact command where the human page shows a Console screenshot | Purely additive. Never the only home of a fact |
| `<ParamField>` / `<ResponseField>` | **Reference pages only** (config, REST API), when those are written | Banned on spine and connector pages |

## Banned, with the reason each

| Banned | Why |
|---|---|
| `<Accordion>`, `<AccordionGroup>`, `<Expandable>` | Collapsed content is under-read (NN/g: "valuable content hidden under an accordion may be missed altogether"), is absent from print and PDF, and Ctrl-F rescue is not reliable — `hidden=until-found` is Chrome 102 but **Firefox 148 / Safari 26.2**, and Russell's field research puts ~90% of users as not knowing Ctrl-F exists. GOV.UK: "do not use the details component to hide information that the majority of your users will need." NN/g's own finding that reluctance to scroll is "a behaviour of the past" removes the motive. **Relocation is a sibling H2 or a sibling page.** |
| `<Tabs>` | Same disclosure problem, plus tab state is not addressable — a support reply cannot link the branch the reader is on. GitLab's own guide: "do not link directly to a single tab." Branches are fork tables plus sibling H2s or sibling pages. |
| `<CodeGroup>` | Provisionally banned on the same addressability grounds and pending the R33 test (does the unselected member ship in the served HTML and in `.md`?). Until someone runs that test, per-platform spellings are **sibling fenced blocks with a bold lead-in**, which always pass. Lift the ban only by recording the test result. |
| `<Visibility for="humans">` | The one Mintlify feature that genuinely deletes information: content wrapped this way "appears on the web page, but not in Markdown output" — it disappears from `.md`, from `llms-full.txt`, and from every agent. For a product whose thesis is serving agents, that is both an information loss and a self-contradiction. |
| `<Tip>` | Advice register. Every tip is either a fact (belongs in prose) or an alternative (belongs in a fork or a late section). The house voice states the cost and the cure declaratively and lets the reader classify. |
| `<Check>` | It is a congratulation with a green box around it, and `## What you have now` may never congratulate. It also competes with `<Warning>` for the same visual budget. |
| `<Danger>` | Three severity tiers dilutes a two-tier system whose rarity is its entire mechanism. The top tier is already `<Warning>` and is already rare. |
| `<Tooltip>` | Hides a definition behind a hover: dead on touch, dead in `.md`, dead in print. |
| Mermaid / `<Panel>` / `<Update>` / `<Banner>` / `<Icon>` | Network-arrow diagram grammar is refused by `soul.md` §9; the others are API-layout, changelog and marketing furniture with no job on these pages. |
| Emoji, badges, decorative dividers | Not the register. |
| Raw `<svg>` in the page body | Ruling 2. |
| `# ` H1 in the body | The H1 comes from frontmatter; a second one breaks the document outline. |
| A hand-written `← back · next →` foot line | Mintlify renders it from the navigation order. `## Next` is the content answer. |

## Two mechanical tests every page must pass before merge

- **The `.md` round-trip.** Fetch the page with `.md` appended (or
  `Accept: text/markdown`) and confirm the prose is complete. Mintlify serves
  clean Markdown at both.
- **Every branch ships in the served HTML.** Fetch the rendered page and grep for
  a string that exists only in a non-default branch. If it is absent, the branch
  is client-rendered and has left the corpus for agents, crawlers and
  find-in-page. **This is the failure mode most likely to pass human review and
  still lose information.** With Tabs and Accordions banned this should pass
  trivially — run it anyway.

---

# §7 · The Start-here spine

Four pages, in this order, in the `Start here` navigation group.

```
start/install              Install Postern
start/open-the-console     Open the Console
start/first-key            Mint your first key
start/connect-an-agent     Connect an agent
```

Then the connectors hang off the fourth as an *or* group.

**Navigation groups in `docs.json`** — this is where the kicker's taxonomy went
(Ruling 1):

| Group | Was | Holds |
|---|---|---|
| `Start here` | `RAISING YOUR GATE` | `index` + the four spine pages |
| `Connect a source` | `CONNECTING A SOURCE` | the nine connector pages |
| `Remote access` | `REACHING YOUR GATE` | the Tailscale page |
| `Hosted clients` | `CHATGPT` | ChatGPT; claude.ai when a witnessed run exists |
| `Reference` | — | grants and sectors, configuration, the ledger — as written |

Every page in every group obeys **R3: complete alone.** A reader landing from
search, or an agent fetching one `.md` with no surrounding nav, must never need to
have read another page to finish. **Duplicate orientation freely** (where the
Console is, what the sidebar sections are called, that a grant covers read and
act). **Never duplicate a value** — ports, redirect URIs, scope strings, image
tags all have one definition and are generated, never retyped.

## 7.1 · `start/install` — Install Postern

**Owns**

- Machine and shell assumption; the Docker installer link; that the machine must
  stay on and that patching is the reader's.
- `git clone https://github.com/getpostern/postern.git && cd postern` — the guide
  currently starts at line 2 and a copy-paste run therefore fails.
- That only `docker-compose.yml` is strictly required, so downloading that one
  file also works.
- The Postgres password: the command, and the three facts a competent reader will
  otherwise "improve" the install into breaking — it must live in `.env` and
  never inline; Postgres bakes it into the data directory on first boot so it can
  never be changed against an existing volume; it must be alphanumeric because it
  is substituted into a connection URL as literal text.
- `docker compose up -d`, and that the first run downloads the published image
  from `ghcr.io/getpostern/postern`.
- **The port facts every later page leans on:** two ports published on loopback —
  **8787** Console, **8788** MCP edge — and the database reachable only over the
  compose network, published nowhere.
- The vault volume `pci_master_key` mounted at `/app/.pci`, the `docker compose
  down -v` `<Warning>`, and that the gateway then refuses to boot fail-closed
  rather than starting green.
- The four everyday compose commands: `ps`, `logs -f app`, `stop`/`start`,
  `pull && up -d`.
- The port-already-allocated recovery, **with the consequence the reader cannot
  guess**: moving the port moves the OAuth redirect URI that the Google,
  Microsoft and WHOOP pages have them register with providers.
- `## Confirm it works`: `docker compose ps`, and the health probe — *blocked on
  house-style §6 · V3; do not publish a curl nobody has run.*

**Must NOT duplicate**

- How to reach the Console from another machine — that is 7.2, in full.
- Anything about keys, sectors, grants or agents — 7.3 and 7.4.
- Any connector.
- Any remote-access procedure.

**Next:** one card → Open the Console.

## 7.2 · `start/open-the-console` — Open the Console

**This page exists because of the founder's ruling that the loopback fact is the
single most important missing fact on the site.** It is not a section of the
install page. A fact that lives in a subsection is a fact a NAS owner never finds
by search; this one needs a title, a URL and a sidebar row.

**Owns**

- **The loopback fact, as the page's first content:** the Console binds
  `127.0.0.1` only and never leaves the machine. State it as the security model,
  not as a limitation — that clause is founder-dictated wording and is reused
  verbatim.
- The fork, which is the page:

  | If… | Then |
  |---|---|
  | Postern runs on the machine you are sitting at | open `http://localhost:8787` |
  | Postern runs on another box — a NAS, a home server, anything headless | tunnel loopback over SSH, then open `http://localhost:8787` in your own browser |

- The tunnel command, verbatim:
  `ssh -N -L 127.0.0.1:8787:127.0.0.1:8787 <your-box>`
- What a fresh Console shows — *"Your gate is new."* — and its top-level map:
  Sources, Agents & keys, The ledger, Settings. **This is the orientation every
  later page is allowed to duplicate freely.**
- **The boundary sentence**, stated explicitly because readers conflate the two:
  reaching the Console and reaching the gate *from an agent* are different
  problems. Remote access publishes the agent-facing edges; the owner's door
  stays on the box either way. Link forward to the Remote access page for the
  first and note that it is optional and off by default.

**Must NOT duplicate**

- Any Tailscale or Funnel procedure. Naming that the page exists is the whole of
  this page's remote-access content.
- Anything about installing, minting, or granting.

**Next:** one card → Mint your first key.

## 7.3 · `start/first-key` — Mint your first key

**Owns**

- Console → Agents & keys → new. Naming the agent (the name is what appears in
  the ledger).
- **Default-deny**: nothing is granted until it is picked. Keep this as text —
  the mint screenshot renders at ~49% and is illegible, `default-deny` is the
  term a technical reader searches for, and for a reader with images off it is
  the only copy of the concept on the page.
- That a grant covers **both reading and acting** on that sector, and that there
  is nothing narrower than a sector.
- The expiry chip and its real default: **Never** on an unpublished gate
  (`apps/web/src/api/exposure.ts:177` `defaultExpiryDays`, pinned by
  `exposure.test.ts:117-120`; 90 only once the gate is published) — and when to
  override it: a key that never leaves this machine may sit at Never; a key that
  will leave it must not.
- **The zero-sector snag**, which is the silent failure a first-timer actually
  hits: the Console does not block minting a key with no sectors. It connects
  successfully and is denied on every read. That is the intended shape, not a
  bug.
- The `<Warning>` **before** the Mint button: the key is shown once, only a hash
  is stored, and the sole remedy is re-mint.
- Revocation semantics — **blocked on house-style §6 · V6**, which is a live
  contradiction between three shipped surfaces. Resolve against the product code
  before writing the sentence.

**Must NOT duplicate**

- The MCP address or any harness configuration — 7.4 owns those.
- The loopback statement beyond a single orientation clause.

**Next:** one card → Connect an agent.

## 7.4 · `start/connect-an-agent` — Connect an agent

**Owns**

- The MCP edge address `http://127.0.0.1:8788/mcp` and the bearer-header form.
- The three-route fork, condition stated first — because the Console's reveal
  screen has two states and a page that leads with "copy the ready-made config"
  strands every reader who does not have one:

  | If the reveal screen… | Then |
  |---|---|
  | shows a ready-made config | copy it, paste into your harness's MCP config, restart |
  | says the gate has no address yet | use the `claude mcp add …` form below — note that the key lands in your shell history |
  | your harness is Claude Desktop | an stdio bridge (`mcp-remote`) in front of the same URL |

- **The hosted-agent precondition, condition before action:** hosted clients
  (claude.ai, ChatGPT) reach you from the vendor's own cloud and can never see
  localhost; nothing is published yet, and **that is the default, not a fault**.
  Publishing one port is the Remote access page; ChatGPT has its own page.
  Without this, the reader clicks through to a Console card saying the bridge is
  off with no idea that this is expected.
- `## Confirm it works`: ask the agent to describe its context, and watch the
  first row land in Console → The ledger under the agent's own name.
  *Blocked on house-style §6 · V1 for any status-code assertion, and on a
  witnessed run for any example response — do not print a fabricated
  `describe_context` reply; it trains a first-timer to reject correct output.*
- **The honest closing fact, which the current guide omits and which makes a
  correct first run look broken:** an agent on a gate with no sources connects
  fine and answers empty. The Console's own screen says *"Add your first
  source."*

**Must NOT duplicate**

- Minting or granting — 7.3.
- The loopback statement beyond one orientation clause.
- Any Tailscale procedure.

**Next:** the connector `<Columns>` — *pick the one you can finish now* — each
card quoting that connector's own cost line. This is the seam where the spine
stops being a sequence.

## 7.5 · Where the loopback fact is restated, and why that is not duplication

A worked example of Ruling 4, because this is the fact the founder called out:

| Page | Form |
|---|---|
| `start/install` | One bullet in Before you start: two ports on loopback, 8787 and 8788, database published nowhere. |
| `start/open-the-console` | The whole page. This is its home. |
| `start/connect-an-agent` | Restated as the hosted-agent precondition, because it is what makes a hosted connection fail. |
| `connect/apple-health` | Restated in Before you start: a quickstart box binds loopback and is unreachable from a phone, so this connector usually wants remote access set up first. |
| `remote/*` | Restated as the boundary: this publishes agent-facing edges; the Console stays on the box. |

Five statements of one fact, none of them redundant, because each fires at a
different moment. A reader who meets it once and needs it three screens later has,
at that moment, not been told.

---

# §8 · Files and naming

```
docs.json                    navigation, theme, fonts — one owner
index.mdx                    the docs home
style.css                    faces docs.json cannot declare
start/<page>.mdx             the spine
start/<page>.ledger.md       its fact ledger — sibling, same basename
connect/<source>.mdx         the connectors
connect/<source>.ledger.md
remote/<page>.mdx
reference/<page>.mdx
images/<file>.png            all screenshots, flat
fonts/<file>.woff2
```

- **Slugs are the reader's words, not ours:** `connect/google`, not
  `connect/guide-05`. No numbers in any path.
- **One `.ledger.md` per `.mdx`, always**, written against the source text before
  a character moves (§9).
- Nothing in this repo is generated. Do not port `build-guides.mjs` here; the
  live site keeps it and stays byte-identical.

---

# §9 · The ledger

**Non-negotiable. A diff that only deletes lines cannot merge.**

Every fact in the source text gets a row **before a single character is cut**.
The file is `<page>.ledger.md`, a sibling of the page. `start/install.ledger.md`
is the worked model — follow its shape.

| col | meaning |
|---|---|
| `id` | stable, e.g. `G05-F14` |
| `fact` | the fact in one sentence — not the prose, the fact |
| `from` | `file:line` of its current home |
| `disposition` | one of the six below |
| `to` | an anchor **that exists at merge time** |
| `instant` | does the reader need this at the same moment as a step? Y/N |
| `evidence` | for `DELETED-REDUNDANT`: `file:line` of the surviving copy, plus rendered scale and alt text if the survivor is a screenshot. For any quoted third-party string: the witness. |
| `sign` | founder ✋ required? |

**Six dispositions:** `KEPT` · `MOVED` (requires a stub at the seam carrying the
fact's headline, not a bare cross-reference) · `DUPLICATED` (orientation only —
**values may never take this disposition**) · `IMPORTED` (cite the product-repo
`file:line` **as read**, and transcribe into this register rather than pasting
README voice) · `NEW` (founder ✋ + a `docs/content-spec.md` changelog row) ·
`DELETED-REDUNDANT`.

**The only legal deletion** is redundancy, and only three things qualify:

1. A restatement of what the screen **legibly** says, with the shot adjacent.
2. Instructions any Docker-running adult already holds ("open your terminal").
3. The same fact stated twice on one page.

**Everything else relocates.** If you cannot decide, it is a relocation. That is
not a tiebreak, it is the rule.

**The instant test.** For every `MOVED` row where `instant = Y`, **the move is
illegal.** A fact needed at instant T that lives behind a click has, at instant
T, been deleted. Stays inline always: the string being pasted · the screenshot of
the control being clicked · the meaning of the error just seen · the warning that
an act is irreversible · the precondition that decides whether the next step will
work · the fact that a secret is about to be shown once, stated **before** the
click that generates it.

**The legibility rider.** A sentence is only redundant with a screenshot if the
screenshot is legible at *rendered* width. A `DELETED-REDUNDANT` row whose
evidence is a screenshot must record the rendered scale and the alt text that
carries the fact, or it is rejected.

**Mislabelling new copy as relocation is the commonest way a fix bypasses the
sign-off it needs.** It happened twice in the source critiques. If no written
home exists anywhere, the disposition is `NEW`.

---

# §10 · Reviewer checklist

Mechanical. Run these; do not eyeball them.

**Structure**

- [ ] Frontmatter has exactly `title` and `description`, and nothing else.
- [ ] `description` ≤ 160 characters, and carries no digit lacking a
      `product-truth.md` row.
- [ ] No `# ` heading anywhere in the body.
- [ ] Nothing between the frontmatter and the `<Info>` block.
- [ ] Exactly one `<Info>` on the page, and it is the first element.
- [ ] **No code fence appears above the `<Info>` block.**
- [ ] Sections appear in order and with these exact headings: `## Choose your
      path` (optional) · steps · `## Confirm it works` · `## If something went
      wrong` · `## What you have now` · `## Next`.
- [ ] `## Next` is the last thing on the page. Nothing follows it.

**Steps**

- [ ] Every `<Step>` has `title`, `titleSize="h2"` and a stable kebab-case `id`.
- [ ] Every step title begins with a verb.
- [ ] Every state-changing step states its observable result in the same
      paragraph as the action.
- [ ] No step opens with a bare verb and no location.
- [ ] No parenthetical beginning "(if you…)" inside a step body.
- [ ] No step body contains a second procedure or a choice.

**Callouts**

- [ ] `grep -c '<Warning' ` ≤ 3, and no two are adjacent.
- [ ] Every `<Warning>` describes something irreversible or silently
      afternoon-costing. If the remedy is "try again", it is a `<Note>`.
- [ ] Warnings about irreversible acts precede the instruction; warnings about
      failures follow it.
- [ ] No `**TRAP**` / `**SNAG**` / any invented label inside a callout.
- [ ] Every literal third-party string in a callout has a named witness in the
      ledger's evidence column.

**Banned strings and components** — one hit fails the build.
**All greps below run over `**/*.mdx` only.** This file, the ledgers and
`README.md` discuss the banned vocabulary by necessity and are excluded; a check
that fires on its own specification gets disabled within a week.

- [ ] `grep -rniE 'field guide|specimen|№|No\. 0|the plate|admission|admit|the keeper|postern door|raising your gate|bring one up' --include='*.mdx' .`
- [ ] `grep -rniE 'simply|just |easy|don.t worry|unfortunately|please note' --include='*.mdx' .`
- [ ] `grep -rE '<Accordion|<Tabs|<Expandable|<Tip|<Check|<Danger|<Tooltip|<CodeGroup|<Mermaid|<Update|<Banner' --include='*.mdx' .`
- [ ] `grep -r 'Visibility for="humans"' --include='*.mdx' .`
- [ ] `grep -rE '<svg' --include='*.mdx' .`
- [ ] `grep -rE 'google-console-gmail\.png|apple-health-card\.png' --include='*.mdx' .`

**Facts**

- [ ] `grep -rE '\b(8787|8788|pci_master_key|/api/oauth/)' --include='*.mdx' .` —
      no value appears as a raw string in two places without a ledger row saying
      why.
- [ ] Every screenshot: `720 ÷ native_width` computed, and the smallest
      fact-bearing text ≥ 11px rendered.
- [ ] Every `<img>` has an `alt` carrying the fact; every `<Frame>` carrying a
      discriminator has a visible `caption`.
- [ ] No real secret, token, password, hostname, account address, or connection
      id anywhere in the diff.

**No-loss**

- [ ] A `.ledger.md` sibling exists and has zero orphans — every removed sentence
      has a row.
- [ ] Every `to` anchor resolves. No forward reference to an unwritten page; if
      the destination does not exist yet, **the fact stays inline.**
- [ ] Read the page with every outbound link treated as dead. If any step becomes
      unrunnable, the page fails R3.
- [ ] `.md` round-trip fetched and prose confirmed complete.

**The last gate.** Three to five people matching the reader profile run the page
screen-shared, unaided, with every stall logged. This is the one that gets
skipped and it is the one that matters: minimalism's measured gains came from
iterative testing at each stage, not from applying the heuristics, and the named
failure mode when that budget is missing is exactly ours — slashing the verbiage
without ever finding out which verbiage was load-bearing. You cannot tell them
apart by introspection, because you already know the answer to every question the
page is failing to answer.

---

# §11 · Open items this template depends on

Carried so they are not lost. None may be resolved by an editor.

**Blocking specific pages**

- **V1** — what the MCP edge answers to an unauthenticated GET. Blocks any status
  code in `start/connect-an-agent`'s confirm section.
- **V2** — where the vault key lives and how it is copied off the box. Blocks any
  backup procedure. Do not write a path nobody has read.
- **V3** — does `/healthz` answer on a port the reader can curl? Blocks
  `start/install`'s confirm section.
- **V6** — the revocation contradiction across three shipped surfaces. Blocks the
  revocation sentence on `start/first-key` and the Reference grants page.
- **R-2** — *"measured cold, healthy in about twenty seconds"* has no
  `product-truth.md` row and is currently shipping in `start/install.mdx`'s
  description. Measure and requalify, or the claim gate the whole site rests on
  is broken by its own documentation.

**Blocking this template**

- **T1 — the `<CodeGroup>` test.** Fetch a rendered Mintlify page containing a
  CodeGroup and grep for a string in a non-selected member, in the HTML and in
  the `.md`. If both contain it, the ban in §6 can be lifted to "per-platform
  spellings of one command, never for branching content". Record the result here.
- **T2 — does `<Step id="…">` produce an anchor?** `titleSize="h2"` guarantees
  one regardless, which is why it is mandatory. If `id` also anchors, keep both;
  if it does nothing, keep it anyway as documentation of intent and link to the
  heading anchor.
- **T3 — the heading `## What you have now`** (§5.8) is the founder's approved
  *"What you will have when you are done"* put into the present tense for its
  position at the end of the page. Confirm or replace.
- **T4 — the print stylesheet.** Nothing in this repo collapses, so the usual
  print loss does not apply, but confirm `<Info>`, `<Warning>` and `<Note>`
  bodies print. A reader provisioning a box from a printed page is real.
