# Lesson 3 — Navigation (`pwd`, `ls`, `cd`, paths, globbing)

- Date: 2026-01-02
- Status: completed
- Goal: move around the filesystem confidently and predictably using absolute/relative paths and safe listing habits

## Recap (From Previous Lesson)
- You learned how to get help reliably using `--help`, `man`, and `apropos`, and how aliases (like `ls=lsd`) can change which help you’re reading.

## Today You’re Learning…
- How to understand “where you are” (`pwd`) and move safely (`cd`).
- How to read directory listings (`ls`) and use hidden files, long format, and human-readable sizes.
- How paths work: absolute vs relative, `.` and `..`, and `~` (home).
- How to match groups of files with globbing (`*`, `?`, `[...]`) without typing every name.

## Topics Covered
- Current directory and `pwd`
- Absolute vs relative paths
- Special path forms: `~`, `.`, `..`
- Listing patterns: `ls`, useful flags, and why `ls` may be `lsd`
- Globbing: `*`, `?`, character sets `[...]`
- Safe navigation habits: tab completion, quoting for spaces, “list before you act”

## Check-in (Answer in Your Own Words)
- What do you most want to be able to do with navigation (find files, move around projects, clean up folders)?
- What feels most confusing right now: paths, `cd`, or reading `ls` output?

## Lesson Flow (Do These In Order)

### 1) Where am I?
What this does: prints the full path to your current directory.

What the parts mean:
- `pwd` = “print working directory”

Run:
- `pwd`

What to look for:
- The path usually starts with `/` (that means it’s an absolute path).

### 2) List what’s here (and don’t assume `ls` is GNU `ls`)
What this does: lists files in the current directory.

What the parts mean:
- `ls` lists entries (on your system it’s an alias to `lsd`)
- `/usr/bin/ls` bypasses the alias and runs GNU `ls`

Run:
- `ls`
- `/usr/bin/ls`

What to look for:
- Differences in formatting and extra info (colors/icons).

### 3) Long listing and hidden files
What this does: shows details like permissions, owner, size, and time, and includes dotfiles.

What the parts mean:
- `-l` long format
- `-a` include entries starting with `.`
- `-h` human-readable sizes (works for GNU `ls`; your `lsd` may differ)

Run:
- `/usr/bin/ls -la`
- `/usr/bin/ls -lah`

What to look for:
- Entries `.` and `..` (current and parent directory).
- Any dotfiles like `.bashrc`, `.zshrc`, `.config` (varies by folder).

### 4) Moving around with `cd`
What this does: changes your current directory.

What the parts mean:
- `cd <path>` changes directory
- `cd` with no args goes to your home directory (`~`)
- `cd -` toggles back to the previous directory

Run:
- `cd`
- `pwd`
- `cd -`
- `pwd`

What to look for:
- How `pwd` changes after each `cd`.

### 5) Absolute vs relative paths
What this does: helps you predict how the shell interprets paths.

What the parts mean:
- Absolute path starts with `/` (from filesystem root)
- Relative path does not start with `/` (from current directory)
- `..` means “parent directory”

Run:
- `pwd`
- `cd ..`
- `pwd`
- `cd -`

What to look for:
- The path one level “up” from where you started.

### 6) Globbing (match many names at once)
What this does: lets the shell expand patterns into lists of filenames before running a command.

What the parts mean:
- `*` matches any string (including empty)
- `?` matches a single character
- `[abc]` matches one character from the set

Run (in a safe practice folder):
- `cd ~/terminal-playground`
- `mkdir -p lesson-03-globbing && cd lesson-03-globbing`
- `touch file1.txt file2.txt fileA.txt notes.md "two words.txt"`
- `/usr/bin/ls -la`
- `echo *.txt`
- `echo file?.txt`
- `echo file[12].txt`
- Optional (see the difference between “one filename with spaces” vs “two arguments”):
  - `printf "<%s>\\n" *.txt`
- Optional (prevent glob expansion by quoting the pattern):
  - `echo "*.txt"`

What to look for:
- Patterns expand to matching filenames.
- If a matched filename contains spaces (like `two words.txt`), it is still a single match; `echo` just prints it with spaces, which can be misleading.
- `?` matches exactly one character (`file?.txt` matches `file1.txt`, `file2.txt`, and `fileA.txt`).
- `[12]` matches a single character from the set (`file[12].txt` matches `file1.txt` and `file2.txt`).

## Notes (Fill During Lesson)
- Your current directory path at the start:
- One thing you noticed about absolute vs relative paths:
- One glob pattern you find useful:

Observed notes:
- Started in: `/home/ajz/Desktop/notes/linux`
- `ls` is `lsd` (icons), while `/usr/bin/ls` is GNU `ls`
- In globbing practice:
  - Created `notex.md` by mistake and fixed it with `mv notex.md notes.md`
  - `echo *.txt` expanded to `file1.txt file2.txt fileA.txt two words.txt`
  - `echo file?.txt` expanded to `file1.txt file2.txt fileA.txt`
  - `echo file[12].txt` expanded to `file1.txt file2.txt`

## Commands Practiced (Append During Lesson)
- `pwd`
- `ls`
- `/usr/bin/ls`
- `/usr/bin/ls -la`
- `/usr/bin/ls -lah`
- `cd`
- `cd -`
- `cd ..`
- `mkdir -p ~/terminal-playground/lesson-03-globbing`
- `cd ~/terminal-playground/lesson-03-globbing`
- `touch file1.txt file2.txt fileA.txt notes.md "two words.txt"`
- `echo *.txt`
- `echo file?.txt`
- `echo file[12].txt`

## Questions Asked (and Answers)
- Q: “Why did `echo *.txt` print `two words.txt` without quotes?”
  - A: Globbing produced one filename that contains a space; `echo` prints its arguments separated by spaces, so it *looks* like two words. Use `printf "<%s>\\n" *.txt` to see each argument clearly.
- Q: “What’s an absolute vs relative path, and what are `.` and `..`?”
  - A: Absolute paths start with `/` (from filesystem root). Relative paths don’t (they’re interpreted from your current directory). `.` means “current directory” and `..` means “parent directory”.

## Exercises (Do Between Lessons)
- From any directory, run `pwd`, then `cd ..`, then `pwd` again and explain the difference.
- In your playground, create 5 files and use `echo *.txt` to see glob expansion.
- Practice `cd -` as a quick “toggle” when moving between two folders.
