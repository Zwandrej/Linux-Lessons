# Lesson 0 — Baseline & Setup

- Date: 2025-12-17
- Status: in progress
- Goal: confirm your environment, safe habits, and your goals for this course

## Recap (From Previous Lesson)
- None (first lesson)

## Recap (This Lesson)
- Set up a safe playground directory for practice and fixed a naming mistake using `mv`.
- Learned how to inspect what a command name resolves to (`type`, `which`, `command -v`) and how to get help (`man`).
- Practiced navigating with `cd`, `..`, and `cd -`, and listing files with `ls -alh`.

## Topics Covered
- Course goal set: daily-use terminal basics (starting ~1/10)
- Safe working style: use a dedicated “playground” folder for practice
- Reading `ls` output: `.` (current dir), `..` (parent dir)
- `ls` options: `-l`, `-a`, `-d` (what they mean and when to use them)
- Shell expansions: `~` (home), brace expansion `{a,b}`
- Redirecting errors: `2>/dev/null` (hide “not found” noise)
- Conditional chaining: `|| true` (don’t treat missing paths as a failure)
- Fixing mistakes safely: prefer rename (`mv`) over delete when possible
- Moving/renaming: `mv <source> <destination>`
- Where am I?: `pwd` prints the current working directory
- Builtins vs external commands: `pwd` is a shell builtin (zsh), `mv` is an external binary
- Getting help: `man <cmd>` works even when the shell uses a builtin
- Pipes and filters (intro): `| head -n 10` to preview output
- Short vs long options: `-x` vs `--long` (convention, not universal)
- Option meaning is per-command: always verify with `man <cmd>` (or builtin docs)
- Reading errors: “no such file or directory” often means a typo in a path
- Seeing external command help: `/usr/bin/pwd --help` shows GNU coreutils options like `-L/--logical` and `-P/--physical`
- Creating directories: `mkdir` and `-p` (create parents; no error if exists)
- Creating files: `touch` (create empty file or update timestamp)
- Listing with useful flags: `ls -a` (all), `-l` (long), `-h` (human sizes)
- Navigation: `cd <dir>` and `cd ..` (parent directory)
- Relative paths: `..` means “parent”; `../dirA` means “sibling directory”
- Jumping back: `cd -` switches to the previous working directory

## Commands Practiced
- `ls -ld ~/{termina-playground,terminal-playground} 2>/dev/null || true`
- `ls -la ~/termina-playground`
- `mv ~/termina-playground ~/terminal-playground`
- `cd ~/terminal-playground/lesson-00`
- `pwd`
- `type mv`
- `type pwd`
- `pwd --help | head -n 10` (learned why this fails for zsh builtin `pwd`)
- `man pwd | head -n 10`
- `which -a pwd`
- `command -v pwd`
- `/user/bin/pwd --help | head -n 10` (typo; should be `/usr/bin/pwd`)
- `/usr/bin/pwd --help | head -n 10`
- `mkdir -p dirA dirB`
- `touch file1.txt file2.txt`
- `ls -alh`
- `cd dirA`
- `cd ..`
- `cd ~/terminal-playground/lesson-00/dirB`
- `cd ../dirA`
- `cd -`

## Questions Asked (and Answers)
- Q: “Can you teach me how to delete a folder?”
  - A: Prefer renaming/moving if it was just a typo. Delete empty dirs with `rmdir`. Delete non-empty dirs with `rm -r` (dangerous; confirm the path first).
- Q: “Explain `mv` and `pwd`.”
  - A: `mv` moves/renames files and folders. `pwd` prints your current directory path.
- Q: “Can you explain what I’m doing before I type new commands?”
  - A: Yes—going forward, each step will include (1) what the command is for, (2) how it’s structured, and (3) what to look for in the output before you run it.
- Q: “What does the `-v` flag mean with `command`?”
  - A: For the shell builtin `command`, `-v` asks “how would the shell resolve this name?” (builtin/function/alias/path). In zsh, for a builtin like `pwd`, it prints `pwd` (not a filesystem path).
- Q: “Why sometimes `-h` and sometimes `--help`?”
  - A: `-x` are typically short options; `--long` are typically long options. It’s a convention (common in GNU tools) but not guaranteed—each command defines its own options, so check `man <cmd>` or the shell’s builtin docs.

## Exercises (Do Between Lessons)
- From anywhere, jump to the playground: `cd ~/terminal-playground/lesson-00`
- Practice “where am I?”: `pwd`, then `cd ..`, then `pwd` again.
- Practice “back”: move between `dirA` and `dirB` using `cd ../dirA`, `cd ../dirB`, and `cd -`.
- Re-list with details: `ls -alh` and explain to yourself what `.` and `..` mean.
