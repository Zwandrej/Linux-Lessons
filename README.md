# Linux Lessons

A step-by-step, Markdown-based course for learning the Linux terminal from basic to intermediate, written as an interactive series of lessons.

## How This Repo Works
- `251217-linux-lesson.md` is the course **index**: curriculum, goals, and progress tracking.
- `lessons/` contains **one Markdown file per lesson**. Each lesson includes:
  - recap from the previous lesson
  - topics covered and commands practiced
  - questions asked (and answers)
  - exercises to practice

## Repo Layout
- `251217-linux-lesson.md` — course index + curriculum
- `lessons/` — lesson notes (chronological)
- `AGENTS.md` — contributor/agent workflow rules

## Getting Started
1. Open `251217-linux-lesson.md` and say **“start lesson”** in the Codex CLI chat.
2. Follow the commands in your terminal.
3. At the end of a lesson, we’ll save a new file in `lessons/` and (optionally) push to GitHub.

## Publishing Lessons to GitHub
Typical flow (from repo root):
```sh
git status
git add -A
git commit -m "docs: add lesson 1"
git push
```

