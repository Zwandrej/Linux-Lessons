# Linux Terminal Course (Basic → Intermediate)

This is your course index. You’ll say **“start lesson”** to begin a new lesson and **“end lesson”** to finish the course. After each lesson I will:
- create/update a new lesson note in `lessons/` (one file per lesson)
- update this index with links, progress, and a short recap pointer

## How We’ll Work (Teacher Rules)
- You type commands in your already-open terminal; I’ll tell you exactly what to run and what to look for.
- If anything looks risky, I’ll mark it clearly before you run it.
- Tell me your OS/distro if you know it (Ubuntu/Fedora/Arch/macOS/WSL). If you don’t, we’ll detect it.
- Ask questions anytime; I’ll capture them in the lesson log.

## Learning Goals
By the end you should be able to:
- navigate and manage files confidently
- read/manipulate text and logs
- find things quickly (files, text, processes)
- understand permissions and ownership
- use pipes/redirection fluently
- troubleshoot with standard CLI tools
- perform common tasks: archives, networking basics, package installs (distro-dependent)
- write small, safe shell scripts

## Curriculum (Suggested Lessons)
Each lesson is ~20–45 minutes. We can skip/reorder based on your needs.

### Module A — Foundations
1. Shell basics: prompt, commands, arguments, quotes, tab completion, history
2. Help system: `man`, `--help`, `info`, `apropos`, `type`, `which`
3. Navigation: `pwd`, `ls`, `cd`, globbing, hidden files, paths

### Module B — Files & Safety
4. Create/move/copy/delete: `mkdir`, `touch`, `cp`, `mv`, `rm` (safe habits)
5. View files: `cat`, `less`, `head`, `tail`, `wc`, `file`
6. Permissions: `chmod`, `chown`, `umask`, executable bit, `sudo` basics

### Module C — Pipes, Redirection, Text Processing
7. Redirection: `>`, `>>`, `<`, `2>`, `|`, `tee`
8. Search text: `rg`/`grep`, `sort`, `uniq`, `cut`, `tr`
9. Find files: `find`, `xargs` (safe patterns), locate database (if available)

### Module D — System Skills
10. Processes & jobs: `ps`, `top`/`htop`, `kill`, `jobs`, `bg`, `fg`, signals
11. Disk & memory: `df`, `du`, `free`, `lsblk` (Linux), mount basics (overview)
12. Networking basics: `ip`/`ifconfig`, `ss`/`netstat`, `curl`, DNS checks
13. Archives & transfers: `tar`, `gzip`, `zip`, `scp`/`rsync` (intro)

### Module E — Shell Environment & Scripting (Intro)
14. Environment: `$PATH`, `env`, `export`, shell startup files, aliases/functions
15. Bash scripting essentials: variables, exit codes, `set -euo pipefail`, `if`, loops
16. Automation patterns: small scripts + cron/systemd timers (overview)

## What I Need From You
When you say “start lesson”, I’ll begin with a 2–3 question check-in:
- What’s your goal (devops? programming? daily use? log reading? servers)?
- How comfortable are you now (0–10)?
- What OS/distro is this terminal on?

## Lesson Log
Lessons live in `lessons/` (one file per lesson). This section is just an index.

### Lesson 0 — Baseline & Setup
- File: `lessons/251217-lesson-00-baseline.md`
- Status: in progress

## Progress Tracker
- [ ] Module A complete
- [ ] Module B complete
- [ ] Module C complete
- [ ] Module D complete
- [ ] Module E complete
