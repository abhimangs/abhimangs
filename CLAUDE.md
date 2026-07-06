# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is `abhimangs/abhimangs` — a GitHub special profile repository. Because the repo name matches the account username, GitHub renders `README.md` directly on the profile page at github.com/abhimangs. There is no application code, no build system, and no tests — every file is either the live profile content or a static asset.

## Workflow

- Autocommit every change without asking for confirmation first.
- Never `git push` unless the user explicitly says "push" in that turn.

## File structure and purpose

- `README.md` — the live profile page. This is the only file that actually renders anywhere; everything else is inert as far as GitHub is concerned (markdown files don't support includes).
- `README_BACKUP.md`, `README_TEST.md`, `coffee.md` — standalone drafts/scratch content, not linked from `README.md` or from each other. Treat edits to these as low-stakes scratch work, not production changes.
- `assets/` — images referenced by markdown files via raw GitHub URLs or relative paths. `assets/buy.png` is used by `coffee.md`. `assets/harvard.png`, `assets/specs.png`, and `assets/spec-new.png` are currently orphaned (not referenced by any markdown file) after the PC-specs section was removed from `README.md` — don't assume they're in use without grepping first.

## Badge/icon conventions

`README.md` mixes two icon sources for the skill/tool rows:

- **skillicons.dev** (`https://skillicons.dev/icons?i=...`) for grouped rows of tech logos. Not every tool has an icon here — an unsupported slug silently renders as a blank/undefined icon instead of erroring. Before adding a new slug, verify it with `curl -s "https://skillicons.dev/icons?i=<slug>" | grep undefined` (empty output = supported).
- **shields.io badges** (`https://img.shields.io/badge/...&logo=<slug>`) for anything skillicons.dev doesn't support, pulling logos from the simple-icons set. Check slug availability against `https://raw.githubusercontent.com/simple-icons/simple-icons/develop/slugs.md` if unsure.

n8n, Zapier, and Make are examples of tools that exist in simple-icons/shields.io but are **not** in skillicons.dev.

## Known third-party service quirk

`README.md`'s GitHub Stats card intentionally points at `github-stats-extended.vercel.app/api`, not `github-readme-stats.vercel.app/api`. The original project is unmaintained and its public demo instance is frequently rate-limited/down; `github-stats-extended` is an actively maintained, query-param-compatible successor. Don't revert to the original `github-readme-stats.vercel.app` domain.
