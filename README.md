# Terminal Dojo 🥋

**Guided, hands-on Linux lessons in the browser.** Terminal Dojo pairs a lesson "scroll" with a live terminal and walks you through **54 belt-ranked kata** — from `pwd` and `ls` all the way up to pipes, command substitution, loops, conditionals, and I/O redirection. Each kata auto-checks the *actual* command you run and its effect on a sandboxed filesystem, then unlocks the next belt.

It runs entirely client-side, with **zero dependencies, no build step, and no network** — and it never touches your real machine.

👉 **[Open `index.html`](./index.html)** in any modern browser. That's it.

## What's inside

The heart of the project is a **shell engine written from scratch** — no libraries. It's not a lookup table of canned answers; it genuinely parses and executes commands:

- **A real in-memory filesystem** — directories, files, symlinks, and permission bits.
- **A command parser** handling authentic shell syntax:
  - flags (`ls -la`, `grep -icn`, `wc -l`, …) and **globbing** (`*.log`, `report?.dat`)
  - **pipes** (`grep ERROR log | wc -l`) and **redirection** (`>`, `>>`, `2>`, `2>&1`, `<`)
  - **command chaining** with exit codes (`mkdir d && cd d`, `cat x || echo fallback`, `;`)
  - **command substitution** `$(...)` and legacy backticks, plus **arithmetic** `$((i + 1))`
  - **environment variables** (`$VAR`, `${VAR}`, `export`, quoting rules) and **background jobs** (`&`, `jobs`, `kill`)
  - control flow: **`for`** / **`while`** loops and **`if … then … else … fi`**
- **~30 emulated Unix commands**: `pwd ls cd cat echo mkdir touch cp mv rm grep wc find sort uniq cut tr sed awk xargs chmod curl jq ln du df ps tar gzip gunzip sleep jobs kill test date man history` — and more.

## The 16 belts

White → Yellow → Orange → Green → Blue → Gold → Purple → Brown → Slate → Red → Rose → Teal → Indigo → Cyan → Steel → Black

Each belt groups a set of kata around a theme (files, inspection, pipes, chaining, text-processing, the wider system, process control, archives, environment variables, loops, control flow, redirection), ending with a master kata that combines everything.

## How it teaches

Every kata defines a task and a **check** that inspects what actually happened — the command you typed *and* the resulting filesystem/output state — so there's no way to fake it. Progress is saved in `localStorage`; the ⟲ button resets it. Light and dark themes are both supported; the terminal screen stays dark either way, like a real one.

## Tech

Single self-contained HTML file. Vanilla JavaScript, no frameworks, no dependencies. The command engine is covered by **65 automated tests** exercising every kata's solution plus the parser's edge cases (quoting, globbing, exit codes, arithmetic, redirection, symlink resolution).

## Deploy

It's a static file — host it anywhere. A `netlify.toml` is included that serves the folder as-is (no build). You can also just open `index.html` locally.
