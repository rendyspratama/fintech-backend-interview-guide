# Fintech Backend Field Guide

A free, searchable reference for senior backend engineering interview prep — built for a global fintech context, but useful for any backend role.

**🔗 Live site:** _add your GitHub Pages URL here once deployed, e.g. `https://yourusername.github.io/fintech-backend-guide/`_

## What this is

A single self-contained HTML file — no build step, no server, no dependencies beyond a font CDN link. Open it locally or visit the live site, and you get:

- **150+ topics** across 18 categories: networking fundamentals, distributed systems, concurrency, databases, reliability, design patterns, security, fintech-specific concerns (double-entry ledgers, PCI-DSS, reconciliation), and more
- Each topic has a plain-language **definition**, a concrete **fintech-grounded example**, and honest **trade-offs** — not just a list of upsides
- **Search** (press `/`) that filters as you type
- **Progress tracking** — mark topics as reviewed, saved locally in your browser
- **Light/dark mode**, sized for comfortable long reading sessions

## Why it exists

Most interview-prep material either stays too abstract ("here's what CAP theorem is") or too shallow (a one-line flashcard). This tries to sit in between: enough depth to actually understand *why* something matters, grounded in examples specific to fintech systems (ledgers, payments, reconciliation, compliance) rather than generic examples that don't transfer to the job.

## Running it locally

There's nothing to install. Download `index.html` and open it in any browser:

```bash
git clone https://github.com/yourusername/fintech-backend-guide.git
cd fintech-backend-guide
open index.html   # or just double-click it
```

## Contributing

This is meant to grow with input from other engineers. If you want to add a topic, fix something inaccurate, or improve an explanation, see **[CONTRIBUTING.md](./CONTRIBUTING.md)** for the format and style guidelines.

Short version: fork the repo, edit the `TOPICS` array in `index.html`, open a Pull Request.

## Scope and honesty note

This content was written to be a strong first-pass study reference, not gospel. Treat it as a starting point — sanity-check anything important before repeating it verbatim in an actual interview, and please open an issue or PR if you spot something wrong.

## License

_Add a license here if you want one — MIT is a common, permissive choice for something like this. Without a license file, default copyright law applies and technically no one can legally reuse your content, which probably isn't what you want for something meant to be openly contributed to._
