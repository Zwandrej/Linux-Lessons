# Lesson 4 — Create/Move/Copy/Delete (Safe Habits)

- Date: 2026-01-02
- Updated: 2026-01-03
- Status: completed
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
-
Session add-on (practical):
- Downloaded apps may not match your CPU architecture (example: `x64` vs `arm64`).
- Old/low-power laptops often have boot quirks (Secure Boot, UEFI vs Legacy).

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
- `cd ~/Downloads`
- `unzip -l <archive.zip>`
- `mkdir -p ~/Applications/<app>`
- `unzip <archive.zip> -d ~/Applications/<app>`
- `file ~/Applications/<app>/*`
- `chmod +x <path-to-executable>`
- `mkdir -p ~/.local/bin`
- `ln -sf <path-to-executable> ~/.local/bin/<name>`
- `rm -rf ~/Applications/<app>` (destructive)
- `rm -f ~/.local/bin/<name>`
- `lsblk -o NAME,SIZE,MODEL,FSTYPE,MOUNTPOINTS`
- `sudo dd if=./image.iso of=/dev/sdX bs=4M status=progress oflag=sync` (destructive)
- `sync`

## Questions Asked (and Answers)
- Q: Where do programs “go” on Linux?
  - A: System-managed installs typically live under `/usr/bin` + `/usr/lib` + `/etc`; local admin installs often use `/usr/local` or `/opt`; user-only installs can live under `~/Applications` with launchers in `~/.local/bin`.
- Q: Do I need to extract a `.zip` before I can run it?
  - A: Yes; you need real files on disk (a directory or an executable) to run or create a launcher pointing at them.
- Q: Why didn’t an app labeled “Linux x64” run?
  - A: Because `x64` means x86_64; on ARM (`aarch64`) you need an `arm64` build (or an emulator, which is slower and may fail for GUI apps).
- Q: Why does a “UEFI: USB” boot option sometimes bounce back to BIOS?
  - A: Often because the firmware can’t load the USB’s bootloader (common causes: Secure Boot, wrong EFI architecture like 64-bit loader on 32-bit UEFI).

## Exercises (Do Between Lessons)
- Create a folder with 3 files, then copy it with `cp -r` and confirm with `/usr/bin/ls -la`.
- Practice renaming files with spaces into hyphenated names using `mv`.
- Explain (out loud) when you’d use `rmdir` vs `rm` vs `rm -r`.
- (Practical) Practice a “downloaded app” workflow: preview an archive, extract to `~/Applications/<app>`, check type with `file`, ensure executable permissions with `chmod +x`, and run with `./program`.
- (Safety) Explain why you should use `lsblk` to identify a USB device before using `dd`.

### In-between mini-session (10–15 min)
Goal: get fast at “verify → act → verify” without risking real files.

Safety note:
- If anything in the path looks unfamiliar, stop and run `pwd` and `/usr/bin/ls -la` before continuing.

1) Get into the practice folder (verify where you are)
What this does: moves you into the safe sandbox directory for Lesson 4.

What the parts mean:
- `cd <path>` changes directories
- `pwd` prints your current directory

Run:
- `cd ~/terminal-playground/lesson-04-files`
- `pwd`
- `/usr/bin/ls -la`

What to look for:
- `pwd` ends with `/lesson-04-files`

2) Make a fresh practice area
What this does: creates a new subfolder so you can repeat this later without confusion.

What the parts mean:
- `mkdir -p` creates directories and won’t error if they already exist

Run:
- `mkdir -p between && cd between`
- `pwd`
- `/usr/bin/ls -la`

What to look for:
- An empty folder (only `.` and `..`)

3) Practice safe copy/move with prompts
What this does:
- Creates a couple files, then copies and renames with confirmation prompts

What the parts mean:
- `touch` creates empty files
- `cp -i` asks before overwriting a destination
- `mv -i` asks before overwriting a destination

Run:
- `touch "two words.txt" alpha.txt`
- `cp -i alpha.txt alpha-copy.txt`
- `mv -i "two words.txt" two-words.txt`
- `/usr/bin/ls -la`

What to look for:
- New files appear, and you understand any prompt you answered

4) Practice directory copy, then safe cleanup
What this does:
- Copies a directory with `cp -r`, then removes only an empty directory with `rmdir`

What the parts mean:
- `cp -r` copies a directory recursively
- `rmdir` removes empty directories only

Run:
- `mkdir docs`
- `touch docs/one.txt docs/two.txt`
- `cp -r docs docs-copy`
- `/usr/bin/ls -la`
- `/usr/bin/ls -la docs-copy`

Optional cleanup (safe):
- `mkdir empty-dir && rmdir empty-dir`

What to look for:
- `docs-copy` exists and contains the same files

### Mini-quiz (answer in your own words)
- What’s the difference between `cp alpha.txt beta.txt` and `cp alpha.txt dirA/`?
- Why is `cp -r` required for directories?
- What are the three checks you do before running `rm -r`?

### In-between practical: unpack, “install”, and run balenaEtcher (from a `.zip`)
Goal: understand where programs live on Linux, how to unpack an archive, and how to run something you downloaded.

#### Where do programs go (quick map)
- System-managed apps (installed by your package manager) usually place files under:
  - `/usr/bin` (main command executables)
  - `/usr/lib` (libraries)
  - `/etc` (system-wide config)
- Locally installed (admin-managed, not from distro packages) often goes under:
  - `/usr/local/bin` (local commands)
  - `/opt/<app>` (vendor apps)
- User-only installs (no `sudo`, safest for learning) usually go under:
  - `~/.local/bin` (your personal commands; often on your `$PATH`)
  - `~/Applications` (a common convention for AppImages/manual apps)

Key idea:
- “Install” can mean “put the executable somewhere sensible and make it runnable.”
- Many downloads are already self-contained executables (common with AppImage); they don’t need a traditional install step.

#### Step 0: confirm what you downloaded
What this does: finds the `.zip` and previews what’s inside before extracting.

What the parts mean:
- `cd` changes directories
- `ls -la` lists files (including hidden) with details
- `unzip -l` lists archive contents without extracting

Run (adjust the filename to match yours):
- `cd ~/Downloads`
- `/usr/bin/ls -la`
- `unzip -l balenaEtcher*.zip`

What to look for:
- The archive contains either an `.AppImage` (common) or a folder like `balenaEtcher-linux-x64/` with an executable inside (also common).

If `unzip` is not installed:
- List contents: `python3 -m zipfile -l balenaEtcher*.zip`

#### Step 1: extract into a dedicated folder
What this does: extracts the `.zip` into its own folder so files don’t scatter in `~/Downloads`.

What the parts mean:
- `mkdir -p` creates a folder (and won’t error if it exists)
- `unzip ... -d <dir>` extracts into a target directory

Run:
- `mkdir -p ~/Applications/etcher`
- `unzip balenaEtcher*.zip -d ~/Applications/etcher`
- `/usr/bin/ls -la ~/Applications/etcher`

What to look for:
- You can see the extracted file(s). If it’s the “folder style” download, you’ll see a folder like `balenaEtcher-linux-x64/`.

If `unzip` is not installed:
- Extract: `python3 -m zipfile -e balenaEtcher*.zip ~/Applications/etcher`

#### Step 2: identify the executable, then make it runnable
What this does:
- Confirms file type
- Adds the executable bit if needed

What the parts mean:
- `file <path>` tells you what kind of file something is
- `chmod +x <file>` makes it executable

Run (use tab completion to fill the exact name):
- `file ~/Applications/etcher/*`
- `chmod +x ~/Applications/etcher/*.AppImage`
- `/usr/bin/ls -la ~/Applications/etcher`

What to look for:
- `file` output mentions `AppImage` (or at least “ELF 64-bit”)
- In `ls -la`, the permissions include an `x` (executable) for the `.AppImage` file

If you extracted a folder like `balenaEtcher-linux-x64/`:
- Identify the launcher: `file ~/Applications/etcher/balenaEtcher-linux-x64/balenaEtcher`
- Ensure it’s runnable: `chmod +x ~/Applications/etcher/balenaEtcher-linux-x64/balenaEtcher ~/Applications/etcher/balenaEtcher-linux-x64/balena-etcher`
- Verify: `/usr/bin/ls -la ~/Applications/etcher/balenaEtcher-linux-x64`

#### Step 3: run it
What this does: launches Etcher directly from the file you extracted.

What the parts mean:
- `./something` runs a program from the current directory (not from `$PATH`)

Run:
- `cd ~/Applications/etcher`
- `./balenaEtcher*.AppImage`

If you extracted a folder like `balenaEtcher-linux-x64/`:
- `cd ~/Applications/etcher/balenaEtcher-linux-x64`
- `./balenaEtcher`

What to look for:
- A GUI window opens.
- If you get a permissions error, re-check `chmod +x ...` from Step 2.

#### Optional: make a friendly command (no `sudo`)
What this does: creates a stable command name like `etcher` you can run from anywhere.

What the parts mean:
- `~/.local/bin` is the standard place for your personal commands
- `ln -s` creates a symlink (a “shortcut” in the filesystem)

Run:
- `mkdir -p ~/.local/bin`
- `ln -sf ~/Applications/etcher/balenaEtcher*.AppImage ~/.local/bin/etcher`
- `etcher`

What to look for:
- `etcher` launches the app.
- If you see “command not found”, your shell may not have `~/.local/bin` on `$PATH` yet (we’ll fix that in the environment lesson).

#### Safety note (important)
- Etcher writes to USB drives; double-check the target drive before flashing.
- If Etcher asks for admin permissions, stop and tell me exactly what prompt you see so we can interpret it safely.

### Practical add-on: making a bootable USB from an ISO (safe checklist)
Goal: write a Linux installer image to a USB without wiping the wrong disk.

Checklist (do this every time):
- Identify the USB device with `lsblk` (look for model + size). The target is the whole disk like `/dev/sdX`, not a partition like `/dev/sdX1`.
- Unmount any mounted USB partitions before writing (if needed): `sudo umount /dev/sdX1`.
- Write the ISO with `dd` (destructive), then run `sync`, then unplug/replug.

Example (replace names):
- ISO path: `~/Downloads/image.iso`
- USB device: `/dev/sdX`

Write:
- `cd ~/Downloads`
- `sudo dd if=./image.iso of=/dev/sdX bs=4M status=progress oflag=sync`
- `sync`

What to look for:
- `dd` reports bytes copied and finishes without errors.

Troubleshooting notes:
- If the machine shows a `UEFI: <USB>` option but boot drops back into BIOS, common causes are Secure Boot being enabled or a mismatch between firmware and the USB’s EFI bootloader architecture.
