# Lesson 1 — Shell Basics (Prompt, Commands, Arguments)

- Date: 2025-12-17
- Status: completed
- Goal: get comfortable running commands, reading prompts, using history + tab completion safely

## Recap (This Lesson)
- Confirmed your environment: Fedora Linux Asahi Remix 42 on aarch64, using `zsh`.
- Learned how the shell splits a command line into a command name plus arguments, and how quoting changes that.
- Practiced safe command inspection (`type`, `command -v`, `which -a`) and discovered your `ls` is an alias to `lsd`.
- Used history (`history`, `!!`) and exit codes (`$?`) to understand success/failure and conditional chaining (`&&`, `||`).
- Created a file with spaces in its name and learned how to refer to it with quotes or escaping.

## Topics Covered
- Command line structure: command name + arguments + options
- Argument splitting on spaces (and why it matters)
- Quoting rules:
  - Double quotes expand variables (`"$HOME"`)
  - Single quotes are literal (`'$HOME'`)
- Seeing arguments with `printf` formatting (`"%s\n"`, `"<%s>\n"`)
- History basics: `history`, history IDs, and `!!`
- Exit codes: `$?`, `0` success, non-zero failure
- Conditional chaining: `cmd && next`, `cmd || fallback`
- Command resolution: alias vs builtin vs external binary; bypassing aliases with `/usr/bin/...` or `command ...`
- Safer path entry: tab completion (intro)

## Check-in (Answer in Your Own Words)
- What’s your goal right now (daily use, programming, DevOps, logs, servers)?
  - Daily use
- Comfort level today (0–10)?
  - 2/10
- What OS/distro is this terminal on (Ubuntu/Fedora/Arch/macOS/WSL)? If unsure, we’ll detect it.
  - Fedora Linux Asahi Remix 42 (Mac M1 / aarch64)

## Lesson Flow (Do These In Order)

### 1) Identify where you are and what shell you’re using
- Run: `pwd`
- Run: `echo "$SHELL"`
- Run: `echo "$0"`
- Run: `uname -a`
- Optional (Linux): `cat /etc/os-release`

### 2) Understand “command + arguments”
- Run: `echo hello`
- Run: `echo one two three`
- Run: `printf "%s\n" one two three`

What you should notice:
- `echo` prints its arguments separated by spaces.
- `printf` uses a *format string* (first argument) to control output; `"%s\n"` means “print a string, then a newline”, repeated for each remaining argument.

### 3) Quoting (why spaces matter)
- Run: `echo hello world`
- Run: `echo "hello world"`
- Run: `echo 'hello world'`
- Run: `echo "home is $HOME"`
- Run: `echo 'home is $HOME'`

What you should notice:
- Without quotes, the shell splits words on spaces into separate arguments (`hello` and `world`), but `echo` prints them back with a space so it *looks* the same.
- Double quotes (`"..."`) keep spaces together as one argument *and* still expand variables like `$HOME`.
- Single quotes (`'...'`) keep spaces together as one argument and treat `$HOME` literally (no variable expansion).

To *see* the difference clearly, `printf "<%s>\n" ...` is handy:
- `printf "<%s>\n" hello world` prints two lines (`<hello>` and `<world>`) because those are two arguments.
- `printf "<%s>\n" "hello world"` prints one line (`<hello world>`) because it is one argument.

### 4) Tab completion and “don’t type long paths”
- In your playground, try: `cd ~/terminal-playground` then type `cd le` and press `<Tab>`
- Type `ls` then press `<Tab>` to see options/files (behavior varies by shell config)

### 5) History (repeat safely)
- Run: `history | tail -n 20`
- Try re-running the last command with the up arrow, then edit it.
- Run: `!!` (repeats previous command; read it first)

What you should notice:
- `history` shows your recent commands with a history ID (the number on the left).
- `!!` expands to “the previous command line” and runs it.
- Use history to save typing, but be careful with commands you don’t fully recognize (especially anything destructive).

### 6) Exit codes (success vs failure)
- Run: `true`
- Run: `echo $?`
- Run: `false`
- Run: `echo $?`

What you should notice:
- Every command “returns” an exit code: `0` means success; non-zero means some kind of failure.
- `$?` is a special shell variable holding the exit code of the *most recent* command.
- This is what makes patterns like `cmd && next` (only run `next` if `cmd` succeeded) and `cmd || fallback` (run fallback if `cmd` failed) work.

Chaining examples:
- `ls alpha.txt && echo "alpha exists"` prints the file then prints the message (because `ls` succeeded).
- `ls does-not-exist && echo "won't print"` does *not* print the message (because `ls` failed).
- `ls does-not-exist || echo "it failed as expected"` prints the message (because `ls` failed).

### 7) Safe “what is this command?”
- Run: `type cd`
- Run: `type ls`
- Run: `which -a ls`
- Run: `command -v ls`

What you should notice:
- A name like `ls` might be an alias/function/builtin, not just `/usr/bin/ls`.
- `which -a` shows every match it can find (including your shell aliases in zsh).
- `command -v` answers “what would the shell run?” (alias/function/builtin/path).

Extra: “what help am I reading?”
- If `ls` is an alias (like `ls=lsd`), then `ls --help` shows the alias target’s help (here: `lsd` help).
- Use an explicit path like `/usr/bin/ls` to see the real GNU `ls` help on your system.

## Notes (Fill During Lesson)
- Prompt: what information it shows on your machine:
- Environment snapshot:
  - `pwd` → `/home/ajz/terminal-playground/lesson-00/dirB`
  - `echo "$SHELL"` → `/usr/bin/zsh`
  - `echo "$0"` → `/usr/bin/zsh`
  - `uname -a` → `Linux ajz 6.17.9-400.asahi.fc42.aarch64+16k #1 SMP PREEMPT_DYNAMIC Fri Nov 28 22:06:07 UTC 2025 aarch64 GNU/Linux`
  - `cat /etc/os-release` → `Fedora Linux Asahi Remix 42 (Forty Two [Adams])`
- Observed output (commands + arguments):
  - `echo hello` → `hello`
  - `echo one two three` → `one two three`
  - `printf "%s\n" one two three` → prints `one`, `two`, `three` on separate lines
- Observed output (quoting):
  - `echo hello world` → `hello world`
  - `echo "hello world"` → `hello world`
  - `echo 'hello world'` → `hello world`
  - `echo "hello is $HOME"` → `hello is /home/ajz`
  - `echo 'hello is $HOME'` → `hello is $HOME`
- Observed output (seeing arguments with `printf`):
  - `printf "<%s>\n" hello world` → `<hello>` then `<world>`
  - `printf "<%s>\n" "hello world"` → `<hello world>`
  - `printf "<%s>\n" 'hello world'` → `<hello world>`
- Observed output (history + exit codes):
  - `history | tail -n 10` → shows your recent commands (IDs 718–727)
  - `false; echo $?` → `1`
  - `true; echo $?` → `0`
  - `history | tail -n 15` → shows your recent commands (IDs 735–749)
  - `!!` → re-ran `history | tail -n 15`
  - `echo $?` → `0`
- Observed output (chaining with exit codes):
  - `ls alpha.txt && echo "alpha exists"` → prints `alpha.txt`, then `alpha exists`
  - `ls does-not-exist || echo "it failed as expected"` → prints an error, then `it failed as expected`
- Observed output (command resolution):
  - `cd` with no args → jumps to your home directory (`~`)
  - `ls` output → indicates `ls` is not plain GNU `ls` (you have an alias)
  - `which -a ls` → shows `ls=lsd` plus multiple `ls` paths (e.g. `/usr/bin/ls`, `/bin/ls`)
  - `command -v ls` → `alias ls=lsd`
  - `type ls` → `ls is an alias for lsd`
  - `type cd` → `cd is a shell builtin`
  - `alias ls` → `ls=lsd`
  - `ls --help | head -n 10` → shows `lsd` help text
  - `/usr/bin/ls --help | head -n 10` → shows GNU `ls` help text
- Most useful completions you discovered:
- Any confusing output/errors:
  - File with spaces: `touch alpha.txt "two words"` created a file named `two words` (spaces included).
  - Escaping spaces: `ls two\ words` works because `\ ` makes the space a literal character inside the argument.
  - Common mistake: `ls does-not exist` is two arguments (`does-not` and `exist`). If you meant one name with a hyphen, use `ls does-not-exist`. If you meant a name with a space, use quotes: `ls "does-not exist"`.
  - Another common mistake: `"won't print"` by itself is not a command; you probably meant `echo "won't print"`.

## Commands Practiced (Append During Lesson)
- `pwd`
- `echo "$SHELL"`
- `echo "$0"`
- `uname -a`
- `cat /etc/os-release`
- `echo hello`
- `echo one two three`
- `printf "%s\n" one two three`
- `echo "hello world"`
- `echo 'hello world'`
- `echo "home is $HOME"`
- `echo 'home is $HOME'`
- `cd ~/terminal-playground`
- `history | tail -n 20`
- `true`
- `echo $?`
- `false`
- `echo $?`
- `type cd`
- `type ls`
- `which -a ls`
- `command -v ls`
- `mkdir -p ~/terminal-playground/lesson-01`
- `cd ~/terminal-playground/lesson-01`
- `pwd`
- `touch alpha.txt "two words"`
- `ls`
- `ls two\ words`
- `history | tail -n 15`
- `!!`
- `echo $?`
- `ls alpha.txt && echo "alpha exists"`
- `ls does-not-exist || echo "it failed as expected"`

## Questions Asked (and Answers)
- Q: “What are `false; echo $?` and `true; echo $?` good for?”
  - A: They demonstrate exit codes (`$?`): `0` means success; non-zero means failure. Exit codes are how the shell and scripts decide what to do next.
- Q: “What is the point of `&&` and `||`?”
  - A: `cmd && next` runs `next` only if `cmd` succeeded; `cmd || fallback` runs `fallback` only if `cmd` failed.
- Q: “Why does `ls --help` show different output than `/usr/bin/ls --help`?”
  - A: Because `ls` is an alias to `lsd` on your system; the full path bypasses the alias and runs GNU `ls`.

## Exercises (Do Between Lessons)
- Practice: use `<Tab>` to complete paths instead of typing full directory names.
- Practice: use history to re-run and edit commands (up arrow, then edit before running).
- Try: run a failing command (like `ls /does-not-exist`) then check the exit code with `echo $?`.
- Create a file with spaces and practice referring to it:
  - `touch "a b.txt"`
  - `ls "a b.txt"`
  - `ls a\ b.txt`
