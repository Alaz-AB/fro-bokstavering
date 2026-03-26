# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page HTML quiz game for practicing Swedish/English radio spelling alphabet (bokstavering) used by FRO (Frivilliga Radioorganisationen). No build tools, no dependencies — just `index.html`.

## Development

Open `index.html` directly in a browser. No build, lint, or test commands exist.

## Architecture

Everything lives in `index.html` — a self-contained file with embedded CSS and JavaScript:

- **DATA object** — All spelling data (letters A-Ö+Ü, digits 0-9, 19 punctuation symbols) with Swedish and English values, sourced from `Minneskort Bokstavering V1.pdf`
- **DISTRACTORS object** — Pre-authored plausible wrong answers per character per language. For letters: names starting with same letter (never spelling variants of the correct word). For digits/punctuation: loosely similar words
- **UI object** — All translatable strings keyed by `sv`/`en`
- **Game state** — Module-level variables (`gameType`, `gameMode`, `lang`, `questions`, etc.)
- **Four screens** — start (type/mode selection), cheatsheet, game (quiz), results (score + error review)

## Key Design Decisions

- **No external dependencies** beyond Google Fonts (Anton + Source Sans 3)
- **Visual design matches fro.se** — navy (#1A2C4B), yellow (#FCCA03), Anton headings
- **Three game types**: mixed (all 59 chars), alphabet only (30 letters), numbers+punctuation (29 chars)
- **Two modes per type**: all characters or limited subset (30/30/15)
- **Distractors are hand-crafted**, not algorithmically generated — stored in DISTRACTORS object
- **No type label shown below characters** during quiz — it leaked answers for punctuation
