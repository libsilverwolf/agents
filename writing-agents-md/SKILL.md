---
name: writing-agents-md
description: Guide for writing AGENTS.md files
license: MIT
metadata:
  author: libsilverwolf <libsilverwolf@outlook.com>
---

# AGENTS.md Guide

This guide defines how to author the `AGENTS.md` file for this project.
Follow it strictly, then place the generated `AGENTS.md` in the project root.

## Create CLAUDE.md also

Writing just `@AGENTS.md` to CLAUDE.md if it doesn't exist to ensure compatibility with Claude.

## Required Sections

An `AGENTS.md` MUST contain the following sections, in order:

1. **Project Summary** — What this project is, in a few sentences.
2. **Tech Stack** — The technologies the project relies on.
3. **Project Structure** — Key directories and files at a glance.
4. **Project Constraints** — MUST follow the template below verbatim.
5. **Common Commands** — Useful commands such as `bun dev`, `bun run build`.

## Project Constraints Template

### Common

- **Never guess.** When a situation is ambiguous, ask the user to confirm
  instead of acting on assumptions. Example: the user asks you to read
  `AGENTS.md`, but the folder only contains `AGENT.md` — verify with the
  user before proceeding.
- **English only in code.** To keep behavior consistent across different
  LLMs, all comments and descriptions in code MUST be written in English.
- **Read nested guides.** Attempt to read the `AGENTS.md` in every directory
  you work on.

### DAO Layer Design

- **Singular model names.** Name model files in singular form
  (e.g. `book.go`, not `books.go`).
- **Shared database singleton.** Design and implement a connection-reusable
  database singleton and share it across the entire app.
- **Free functions over structs/classes (Go / Rust / Node.js).** Do NOT
  implement data-access actions inside a struct or class. Write standalone
  functions that take the connection as an explicit argument, e.g.:

  ```go
  func get_book(db: DbConnection, book_id: int) { ... }
  ```