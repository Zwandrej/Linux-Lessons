# Lesson 4 — Create/Move/Copy/Delete (Safe Habits)

- Date: 2026-01-02
- Status: in progress
- Goal: create, copy, move, and delete files/directories safely using “list before you act” habits

## Recap (From Previous Lesson)
- You learned navigation: `pwd`, `cd`, absolute vs relative paths, and globbing patterns like `*` and `?`.

## Today You’re Learning…
- How to create files/folders (`mkdir`, `touch`) and understand what they actually do.
- How to copy/move safely (`cp`, `mv`) and avoid accidental overwrites.
- How to delete safely (`rm`, `rmdir`) and recognize risky patterns.

## Safety Rules (Non-Negotiable)
- Always run `pwd` before a delete/move if you feel unsure.
- Prefer “list the target” first: `/usr/bin/ls -la <path>`.
- Use tab completion to avoid typos.
- When deleting, start with the least-destructive command:
  - empty dir → `rmdir`
  - file → `rm`
  - non-empty dir → `rm -r` (dangerous; stop and verify)

## Lesson Flow (Do These In Order)

### 1) Create a safe practice folder
What this does: creates a dedicated place to practice without touching important files.

What the parts mean:
- `mkdir` creates directories
- `-p` creates parent dirs as needed and won’t error if it already exists
- `&&` only runs the next command if the previous succeeded

Run:
- `mkdir -p ~/terminal-playground/lesson-04-files && cd ~/terminal-playground/lesson-04-files`
- `pwd`
- `/usr/bin/ls -la`

What to look for:
- `pwd` ends with `/lesson-04-files`
- Directory listing shows `.` and `..` and (initially) no files

### 2) Create files (`touch`) and folders (`mkdir`)
What this does:
- `touch` creates empty files (or updates timestamps if they exist)
- `mkdir` creates folders

Run:
- `touch alpha.txt beta.txt "two words.txt"`
- `mkdir dirA dirB`
- `/usr/bin/ls -la`

What to look for:
- Files and directories appear; the one with spaces should display as `two words.txt`

### 3) Copy files (`cp`) vs copy directories (`cp -r`)
What this does:
- `cp <src> <dst>` copies a file
- `cp -r <dir> <dst>` copies a directory recursively

Run:
- `cp alpha.txt alpha-copy.txt`
- `cp -r dirA dirA-copy`
- `/usr/bin/ls -la`

What to look for:
- New copies exist; `dirA-copy` is a directory

### 4) Move/rename (`mv`) and the “overwrite risk”
What this does:
- `mv` renames (within a directory) or moves (to another directory)
- If the destination exists, `mv` may overwrite it depending on options/shell settings, so we’ll be careful

Run:
- `mv beta.txt dirA/`
- `mv "two words.txt" two-words.txt`
- `/usr/bin/ls -la`
- `/usr/bin/ls -la dirA`

What to look for:
- `beta.txt` is now inside `dirA`
- `two-words.txt` exists (renamed from the spaced name)

### 5) Delete: `rmdir` (empty dirs) first, then `rm` (files)
What this does:
- `rmdir` removes empty directories only (safer)
- `rm` removes files

Run:
- `rmdir dirB`
- `rm alpha-copy.txt`
- `/usr/bin/ls -la`

What to look for:
- `dirB` is gone; `alpha-copy.txt` is gone

### 6) The dangerous one: `rm -r` (non-empty directories)
Stop here before running anything destructive. We’ll practice “verify first”.

Verify (safe):
- `/usr/bin/ls -la`
- `/usr/bin/ls -la dirA`

If you later decide to remove a non-empty directory, we’ll do it with a checklist first.

## Notes (Fill During Lesson)
- Any surprises with `mv` or `cp`:
- Any errors you hit:

## Commands Practiced (Append During Lesson)
- `mkdir -p ~/terminal-playground/lesson-04-files`
- `cd ~/terminal-playground/lesson-04-files`
- `pwd`
- `/usr/bin/ls -la`
- `touch alpha.txt beta.txt "two words.txt"`
- `mkdir dirA dirB`
- `cp alpha.txt alpha-copy.txt`
- `cp -r dirA dirA-copy`
- `mv beta.txt dirA/`
- `mv "two words.txt" two-words.txt`
- `rmdir dirB`
- `rm alpha-copy.txt`

## Questions Asked (and Answers)
- Q:
  - A:

## Exercises (Do Between Lessons)
- Create a folder with 3 files, then copy it with `cp -r` and confirm with `/usr/bin/ls -la`.
- Practice renaming files with spaces into hyphenated names using `mv`.
- Explain (out loud) when you’d use `rmdir` vs `rm` vs `rm -r`.

