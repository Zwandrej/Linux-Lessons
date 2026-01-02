# Lesson 2 — Help System (`man`, `--help`, `info`, `apropos`)

- Date: 2026-01-02
- Status: completed
- Goal: quickly find accurate help for any command (including aliases/builtins) and learn how to read `man` pages efficiently

## Recap (From Previous Lesson)
- You learned how the shell parses commands + arguments, how quoting changes splitting, and how to inspect what a name resolves to (`type`, `command -v`, `which -a`).
- You discovered `ls` is an alias to `lsd` on your system, so `ls --help` may not be the help you expect.

## Today You’re Learning…
- How to get help fast without guessing flags (why it matters: safer commands, fewer mistakes).
- How to use `man` effectively (searching, jumping, and quitting).
- How to choose the right help source: `man` vs `--help` vs `info` vs “search the man database”.

## Topics Covered
- The “help ladder”: start with `type`, then `--help`, then `man`, then `info`, then search (`apropos` / `man -k`)
- Aliases/builtins and why help can differ from `/usr/bin/<cmd>`
- Reading `man` pages: sections, SYNOPSIS, options, exit status, examples
- Searching: inside `man` (`/pattern`) and across man pages (`apropos`, `man -k`)

## Lesson Flow (Do These In Order)

### 1) Confirm what command you’re actually running
What this does: tells you whether a name is an alias, function, builtin, or external binary.

What the parts mean:
- `type <name>` asks the shell “what is this?”
- `command -v <name>` asks “what would run if I typed this?”
- `which -a <name>` lists all matches in your `PATH` (and may show aliases in zsh)

Run:
- `type ls`
- `command -v ls`
- `which -a ls`

What to look for:
- If you see `alias ls=...`, then `ls --help` and `man ls` may describe different programs.

### 2) Use `--help` for a quick overview (when it exists)
What this does: prints a short usage summary and common options (often faster than `man`).

What the parts mean:
- `--help` is a *convention* (common in GNU tools), not guaranteed.
- Use a full path like `/usr/bin/ls` to bypass an alias like `ls=lsd`.

Run:
- `ls --help | head -n 15`
- `/usr/bin/ls --help | head -n 15`

What to look for:
- Whether the output matches `lsd` vs GNU `ls` (this confirms you’re reading the right docs).

### 3) Read a `man` page (and learn the controls)
What this does: opens the manual page in a pager (usually `less`).

What the parts mean:
- `man <topic>` opens the manual entry for that topic.
- Inside `man`/`less`:
  - `q` quit
  - `/pattern` search forward, then `n` next match, `N` previous match
  - `Space` page down, `b` page up

Run:
- `man ls`

What to look for:
- Find the `SYNOPSIS` section and explain in your own words what brackets like `[...]` usually mean (“optional”).
- Search for “`--color`” with `/--color` (or any option you’re curious about).

### 4) Learn about man page sections (`man 1`, `man 5`, `man 8`)
What this does: chooses a specific manual section when multiple pages share the same name.

What the parts mean (common ones):
- `1` user commands (most CLI tools)
- `5` file formats and config files
- `8` admin/system commands

Run:
- `man man`
- `man 5 passwd`

What to look for:
- Notice how `passwd(5)` is a *file format* description, not the `passwd(1)` command.

### 5) Use `info` when it’s available (GNU manuals)
What this does: opens GNU “Info” documentation (sometimes more detailed/tutorial-like than `man`).

Run:
- `info coreutils 'ls invocation'` (if it works)
- If that fails: `info ls` (or skip)

What to look for:
- Whether `info` provides more narrative/examples than `man`.

### 6) Search for help by keyword (`apropos` / `man -k`)
What this does: searches the man-page database by keyword when you don’t know the command name.

Run:
- `apropos permissions | head -n 10`
- `man -k archive | head -n 10`

What to look for:
- Useful candidate commands you can then open with `man <name>`.
- If you get “nothing appropriate”, your man database might be limited; we can work around it.

## Notes (Fill During Lesson)
- Any `man` navigation tips that felt natural:
- Any confusing help output:

## Commands Practiced (Append During Lesson)
- `type ls`
- `command -v ls`
- `which -a ls`
- `ls --help | head -n 15`
- `/usr/bin/ls --help | head -n 15`
- `man ls`
- `man man`
- `man 5 passwd`
- `info coreutils 'ls invocation'`
- `info ls`
- `apropos permissions | head -n 10`
- `man -k archive | head -n 10`

## Questions Asked (and Answers)
- Q: “Why does `ls --help` differ from `/usr/bin/ls --help`?”
  - A: Because `ls` is an alias to `lsd` on your system; the full path bypasses aliases and shows GNU `ls` help.
- Q: “What does `LS(1)` mean in `man ls`?”
  - A: It’s the manual section: `1` is user commands. Other common ones are `5` (file formats) and `8` (admin commands).
- Q: “What do `[...]` and `{...}` usually mean in man pages?”
  - A: `[...]` means optional; `{...}` usually means “choose one of these” (a required choice).

## Exercises (Do Between Lessons)
- Pick 2 commands you used recently and find one option for each using `man` (not web search).
- Use `apropos` to find a tool related to “disk” or “network”, then open its man page.
- Open `man ls` and practice searching for options using `/` and `n`, then quit with `q`.
