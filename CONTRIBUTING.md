# Contributing to the Fintech Backend Field Guide

Thanks for wanting to add to this. It's just one HTML file — all the content lives in a single JavaScript array called `TOPICS`, near the top of the `<script>` section. No build step, no dependencies. You edit `index.html` directly.

## Quick start

1. **Fork** this repo (button top-right of the GitHub page).
2. Open `index.html` in a text editor.
3. Find the `TOPICS` array (search for `const TOPICS = [`).
4. Add your new topic as a new object in that array (format below).
5. Open `index.html` in your browser locally to check it renders correctly and reads well.
6. Commit, push to your fork, and open a **Pull Request** back to this repo.

No need to touch any HTML/CSS unless you're changing the app itself, not the content.

---

## The topic format

Every topic is one JavaScript object with this shape:

```js
{cat:"DB", title:"Your Topic Title", def:`...`,
diagram:`<svg viewBox="0 0 480 200" ...>...</svg>`,
ex:`...`,
trade:[`...`, `...`]},
```

Field by field:

| Field | Required? | What it is |
|---|---|---|
| `cat` | Yes | A category code (see list below). Must match one of the existing `CATEGORIES` codes. |
| `title` | Yes | Short, specific title. Must be unique — no duplicate titles anywhere in the file. |
| `def` | Yes | The definition/explanation. See style rules below. |
| `diagram` | No | Optional, but the norm — nearly every topic in the guide has one. A raw SVG string. See "Diagrams" below before adding one. |
| `ex` | Yes | A concrete example, ideally grounded in a fintech scenario. |
| `trade` | Yes | An array of trade-off strings (1 or more). Each string is one bullet point. |
| `code` | No | Optional. A code snippet (see Code Examples below). Only add this if a code example genuinely clarifies the concept — most topics don't need one. |
| `related` | No | Optional. An array of *exact* titles of other topics this one connects to (rendered as a "See Also" list). Usually added by a maintainer during review rather than by the PR author — picking good cross-links needs a view of the whole 178-topic guide, which a first-time contributor won't have. Feel free to suggest a couple in your PR description if an obvious connection comes to mind, but don't feel obligated to fill this in yourself. |
| `priority` | No | Optional. Set to `"high"` to flag a topic as high-yield for interview prep. Also maintainer-curated for the same reason as `related` — it's a judgment call made in the context of the whole guide, not a per-topic decision. |

Note: you'll also see an `id` field on topics at runtime — that's generated automatically by the app from `cat` + array position. Never set it yourself.

### Existing category codes

```
CS  Programming & CS Fundamentals
NW  Networking Fundamentals
DS  Distributed Systems
TS  Thread Safety
CA  Concurrency in Applications
CD  Concurrency in Databases
DB  Database Theory & Design
CP  Core Principles & Paradigms
RS  Reliability & Stability
PT  Design Patterns
TE  Testing Strategy
CH  Caching Strategies
MA  Messaging, APIs & Serialization
SC  Security Fundamentals
MR  Multi-Region, LB & DR
FT  Fintech-Specific
PF  DB Performance at Scale
DG  Debugging Production
CC  Cloud, CI/CD & Containers
```

If your topic doesn't fit any existing category, propose a new one — open an issue first to discuss it before submitting a PR, since it also means adding an entry to the `CATEGORIES` array.

---

## Style rules (please actually follow these — they exist because of real feedback)

**1. No dense, run-on definitions.** If your definition covers more than one sub-concept (like explaining 3 types of something, or spelling out an acronym), break each one onto its own line using a blank line between them. Do this:

```js
def:`Three ways to do X.

First approach — explanation here.

Second approach — explanation here.`
```

Not this:

```js
def:`First approach: explanation. Second approach: explanation. Third approach: explanation.`
```

**2. If it's an acronym, spell out what each letter stands for before explaining the concept.** Don't assume the reader already knows. (This guide got this wrong for CAP theorem once — don't repeat that mistake.)

**3. Use plain, everyday words.** Avoid unnecessarily academic phrasing. If you can explain it the way you'd explain it out loud to a coworker, that's the right register. Avoid jargon without a plain-language explanation attached.

**4. The example should be a real, concrete scenario** — ideally fintech-flavored (payments, ledgers, accounts, transactions, compliance) since that's this guide's focus — not an abstract "imagine you have object A and object B."

**5. Trade-offs should be genuine trade-offs**, not just a list of benefits. Include the real cost, limitation, or "when NOT to use this" alongside the upside.

**6. Keep it factually accurate.** If you're not sure about a detail, say so in the PR description so a reviewer can double check, rather than guessing confidently.

---

## Diagrams

Nearly every topic in the guide (currently all 178) has a `diagram` — a hand-written SVG string. It's optional in the schema, but treat it as the norm, not the exception.

**1. Every color must be a CSS variable, never a literal hex value.** Use `var(--ledger)`, `var(--text-dim)`, `var(--border)`, etc. — never `#4ECE94` or similar. The whole app supports a light/dark theme toggle, and a literal hex color will look wrong (or invisible) in one of the two modes.

**2. Match the existing visual restraint.** One accent color at rest, generous whitespace, no more than 2-3 colors active in a single diagram. A previous attempt at a busier, multicolor diagram was rejected on sight as "not proper" for this guide's aesthetic. Before designing a new one, open 2-3 existing diagrams in the file and match their style rather than inventing a new visual language.

**3. If you use `marker-end="url(#some-id)"` for an arrowhead, make sure a matching `<defs><marker id="some-id">...</marker></defs>` block exists *inside that same diagram's own string.* This has been a real, repeated bug — a marker ID copy-pasted from one diagram without its matching `<defs>` block, breaking silently. Before considering a diagram done, grep your own new diagram string for every `url(#...)` reference and confirm the matching `<defs>` entry is there.

**4. If a diagram depicts a real mathematical relationship** (a growth curve, a distribution, anything with a formula — like the Big-O complexity chart), compute the coordinates from the actual formula rather than hand-placing points that "look about right." A wrong-shaped curve is worse than no diagram.

**5. Never have two `diagram:` fields on the same topic.** JavaScript object literals allow duplicate keys with no error — the last one silently wins and the first becomes dead, wasted code. This has happened before (3 topics had it, fixed in a later cleanup pass). If you're revising a topic that already has a diagram, edit the existing field; don't add a second one.

---

## Code examples

If you're adding a `code` field:

- Keep snippets short and illustrative, not production-grade or complete.
- Avoid using backtick characters (`` ` ``) anywhere inside the code string — since the whole field is itself wrapped in backticks in JavaScript, a stray backtick inside will break the file. Use regular quotes in your example code instead.
- Add a couple of inline comments explaining the *why*, not just the *what* — the existing Saga and 2PC examples are good references for the style.
- Label the language honestly; the renderer currently labels all code blocks "Go" — if you're adding a non-Go example, mention this in your PR so the label can be made dynamic.

---

## Checklist before opening a PR

- [ ] My topic's `cat` matches an existing category code exactly (case-sensitive).
- [ ] My `title` doesn't already exist elsewhere in the file.
- [ ] My `def` uses line breaks for multi-part explanations (no run-on lists).
- [ ] My `ex` is a concrete, ideally fintech-grounded scenario.
- [ ] My `trade` array includes real downsides, not just upsides.
- [ ] If I added a `diagram`, every color is a CSS variable (no literal hex), and every `marker-end="url(#x)"` has a matching `<defs><marker id="x">` in that same diagram string.
- [ ] My topic has only one `diagram` field, not two.
- [ ] I opened `index.html` in a browser and confirmed my topic displays correctly, search finds it, and nothing else broke.
- [ ] No stray backticks inside any of my template literal strings.

## Reporting a mistake instead of fixing it yourself

Don't want to submit a PR? Open an **Issue** instead, quote the topic title and the part that's wrong, and explain what should change. That's just as valuable as a PR.

## What NOT to submit

- Duplicate topics covering the same concept as an existing one (suggest an edit to the existing topic instead).
- Content unrelated to backend engineering / fintech systems.
- Marketing content, affiliate links, or anything promotional.
- Copyrighted material copied verbatim from another source (blog posts, docs, books) — write it in your own words.
