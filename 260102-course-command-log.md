# Linux Terminal Course — Command Log

This file is a running list of commands learned/practiced during the course. Append new commands at the end of the relevant lesson section.

## Lesson 0 — Baseline & Setup
- `ls -ld ~/{termina-playground,terminal-playground} 2>/dev/null || true`
- `ls -la ~/termina-playground`
- `mv ~/termina-playground ~/terminal-playground`
- `cd ~/terminal-playground/lesson-00`
- `pwd`
- `type mv`
- `type pwd`
- `pwd --help | head -n 10`
- `man pwd | head -n 10`
- `which -a pwd`
- `command -v pwd`
- `/usr/bin/pwd --help | head -n 10`
- `mkdir -p dirA dirB`
- `touch file1.txt file2.txt`
- `ls -alh`
- `cd dirA`
- `cd ..`
- `cd ~/terminal-playground/lesson-00/dirB`
- `cd ../dirA`
- `cd -`

## Lesson 1 — Shell Basics (Prompt, Commands, Arguments)
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
- `touch alpha.txt "two words"`
- `ls`
- `ls two\\ words`
- `history | tail -n 15`
- `!!`
- `ls alpha.txt && echo "alpha exists"`
- `ls does-not-exist || echo "it failed as expected"`

## Lesson 2 — Help System (`man`, `--help`, `info`, `apropos`)
- `type ls`
- `command -v ls`
- `which -a ls`
- `ls --help | head -n 15`
- `/usr/bin/ls --help | head -n 15`
- `man ls`
- `man man`
- `man 5 passwd`
- `apropos permissions | head -n 10`
- `man -k archive | head -n 10`
- `man tar`

## Lesson 3 — Navigation (`pwd`, `ls`, `cd`, paths, globbing)
- `pwd`
- `ls`
- `/usr/bin/ls`
- `/usr/bin/ls -la`
- `/usr/bin/ls -lah`
- `cd`
- `cd -`
- `cd ..`
- `mkdir -p lesson-03-globbing && cd lesson-03-globbing`
- `touch file1.txt file2.txt fileA.txt notes.md "two words.txt"`
- `mv notex.md notes.md`
- `echo *.txt`
- `echo file?.txt`
- `echo file[12].txt`
- `printf "<%s>\\n" *.txt`

