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
ex:`...`,
trade:[`...`, `...`]},
```

Field by field:

| Field | Required? | What it is |
|---|---|---|
| `cat` | Yes | A category code (see list below). Must match one of the existing `CATEGORIES` codes. |
| `title` | Yes | Short, specific title. Must be unique — no duplicate titles anywhere in the file. |
| `def` | Yes | The definition/explanation. See style rules below. |
| `ex` | Yes | A concrete example, ideally grounded in a fintech scenario. |
| `trade` | Yes | An array of trade-off strings (1 or more). Each string is one bullet point. |
| `code` | No | Optional. A code snippet (see Code Examples below). Only add this if a code example genuinely clarifies the concept — most topics don't need one. |

### Existing category codes

```
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
- [ ] I opened `index.html` in a browser and confirmed my topic displays correctly, search finds it, and nothing else broke.
- [ ] No stray backticks inside any of my template literal strings.

## Reporting a mistake instead of fixing it yourself

Don't want to submit a PR? Open an **Issue** instead, quote the topic title and the part that's wrong, and explain what should change. That's just as valuable as a PR.

## What NOT to submit

- Duplicate topics covering the same concept as an existing one (suggest an edit to the existing topic instead).
- Content unrelated to backend engineering / fintech systems.
- Marketing content, affiliate links, or anything promotional.
- Copyrighted material copied verbatim from another source (blog posts, docs, books) — write it in your own words.
