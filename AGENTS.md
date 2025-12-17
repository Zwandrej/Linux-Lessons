# Repository Guidelines

This directory is a lightweight, Markdown-first learning notebook for Linux terminal lessons. Keep changes focused on clarity and continuity of the course, and publish lessons incrementally to GitHub.

## Project Structure & Module Organization
- `./251217-linux-lesson.md`: Course index (curriculum, progress, and links to lesson files).
- `./lessons/`: One Markdown file per lesson (append-only history; avoid rewriting past lesson content unless correcting factual mistakes/typos).
- `./AGENTS.md`: Contributor/agent guide for maintaining this folder.
- Additional notes (optional): prefer date-prefixed files like `YYMMDD-topic.md` (e.g., `251218-permissions.md`) to keep lessons discoverable.

## Build, Test, and Development Commands
There is no build system in this folder.
- Preview in terminal: `less 251217-linux-lesson.md`
- Quick search: `rg -n "Lesson" .`
- (Optional) Lint Markdown if installed: `markdownlint "**/*.md"`
- (Optional) Export to PDF/HTML if installed: `pandoc 251217-linux-lesson.md -o out.html`

## Coding Style & Naming Conventions
- Markdown style:
  - Use headings (`#`, `##`, `###`) for structure; avoid deep nesting.
  - Use `-` for bullets; keep bullets short and action-oriented.
  - Wrap commands, paths, and identifiers in backticks (e.g., `ls -la`, `~/notes`).
  - Prefer one blank line between sections; avoid trailing whitespace.
- Naming:
  - Files: `YYMMDD-<topic>.md` (kebab-case topic).
  - Lessons: “Lesson N — Title” and append chronologically.

## Testing Guidelines
No automated tests are defined. Validate by:
- ensuring Markdown renders cleanly in your editor/viewer
- checking links/paths and command examples for correctness

## Commit & Pull Request Guidelines
Use Conventional Commits, e.g., `docs: add lesson 1` or `docs: refine curriculum`.
PRs (if applicable): include a brief summary, what changed in the lesson notes, and any new exercises added.

## Lesson Workflow (Important)
At the end of each lesson:
1. Create/update the lesson note: `lessons/YYMMDD-lesson-NN-<topic>.md`
2. Update `251217-linux-lesson.md` to link the new lesson file and update checkboxes if a module is complete.
3. Record:
   - recap
   - topics covered
   - commands practiced
   - questions asked (and answers)
   - exercises
4. Publish to GitHub at the end of every lesson (from repo root):
   - `git add -A`
   - `git commit -m "docs: add lesson NN"`
   - `git push`

## Teaching Preference (Important)
- Before asking the learner to run a command, first explain: (1) what it does, (2) what the parts mean, and (3) what to look for in the output.
- At the start of each lesson, give a short “today you’re learning…” overview (skills + why it matters).
- When introducing commands/arguments, include practical use cases (what problems this helps solve) and common patterns (e.g., one command + multiple arguments, quoting for spaces).

## Security & Safety Notes
- Do not record secrets (tokens, passwords, SSH private keys) in notes.
- When adding command examples, prefer safe defaults and clearly label destructive commands (e.g., `rm`, `chmod -R`, `sudo`).
