# Fintech Backend Field Guide

A free, searchable reference for senior backend engineering interview prep — built for a global fintech context, but useful for any backend role.

**🔗 Live site:** 
([Doc site](https://rendyspratama.github.io/fintech-backend-interview-guide/)).


## What this is

A single self-contained HTML file — no build step, no server, no dependencies beyond a font CDN link. Open it locally or visit the live site, and you get:

- **178 topics** across 19 categories: CS/programming fundamentals, networking, distributed systems, concurrency, databases, reliability, design patterns, security, fintech-specific concerns (double-entry ledgers, PCI-DSS, reconciliation, payment rails, ledger design), and more
- Each topic has a plain-language **definition**, often a **diagram**, a concrete **fintech-grounded example**, and honest **trade-offs** — not just a list of upsides
- **Search** (press `/`) that filters as you type, plus a **command palette** (`⌘K` / `Ctrl+K`) to jump straight to any topic by title
- **Filter the sidebar** by High-Yield, Starred, Unreviewed, or Weak Spots — combine any of them
- **See Also** links connecting related topics, so you can follow a concept across categories
- **High-Yield tags** flagging the topics most likely to come up under interview time pressure
- **Recall Mode** — active-recall practice (title first, definition hidden until you reveal it) with real spaced repetition: topics you keep missing come back more often across sessions, ones you've nailed repeatedly taper off
- **Bookmarks and personal notes** per topic, plus progress tracking — all saved locally in your browser
- **Light/dark mode**, sized for comfortable long reading sessions

## Why it exists

Most interview-prep material either stays too abstract ("here's what CAP theorem is") or too shallow (a one-line flashcard). This tries to sit in between: enough depth to actually understand *why* something matters, grounded in examples specific to fintech systems (ledgers, payments, reconciliation, compliance) rather than generic examples that don't transfer to the job.

## Running it locally

There's nothing to install. Download `index.html` and open it in any browser:

```bash
git clone https://github.com/rendyspratama/fintech-backend-interview-guide.git
cd fintech-backend-interview-guide
open index.html   # or just double-click it
```

## Contributing

This is meant to grow with input from other engineers. If you want to add a topic, fix something inaccurate, or improve an explanation, see **[CONTRIBUTING.md](./CONTRIBUTING.md)** for the format and style guidelines.

Short version: fork the repo, edit the `TOPICS` array in `index.html`, open a Pull Request.

## Scope and honesty note

This content was written to be a strong first-pass study reference, not gospel. Treat it as a starting point — sanity-check anything important before repeating it verbatim in an actual interview, and please open an issue or PR if you spot something wrong.

## License

_Add a license here if you want one — MIT is a common, permissive choice for something like this. Without a license file, default copyright law applies and technically no one can legally reuse your content, which probably isn't what you want for something meant to be openly contributed to._
