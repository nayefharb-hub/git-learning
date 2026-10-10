# git-learning — CLAUDE.md

This repo is my Git & GitHub classroom, run with Matt Pocock's `teach` skill (`.claude/skills/teach/`). Start every learning session with `/teach`.

## Environment
Windows laptop, Git Bash (not PowerShell) — give every command in Bash syntax. Local path: `C:\Users\user\projects\git-learning`.

## Who I am and why
PMO lead, not a developer. Claude Code does the git work in my real repos (Business-Case-Template, gantt-dashboard, Competency-Assessment-Platform). Here I learn to supervise it, do the everyday loop myself, and rescue mistakes. MISSION.md has the detail.

## This repo is public — basic hygiene
Real repo and branch names are fine to use here (PLAN.md does). What's never allowed in anything committed to this repo: actual secret values — API keys, tokens, passwords, `.env` file contents, connection strings — from any of my repos. Describing that a secret exists, or that a check caught one, is fine; pasting the value itself is not.

## PLAN.md is the syllabus
- `PLAN.md` is my mastery plan: phases, primary resources, proof tasks and gates. Follow it; don't invent a different curriculum.
- `NOTES.md` has a line `Current phase: N — next gate: task X`. Before choosing a lesson, read that line, the latest learning records, and the matching phase in PLAN.md. Teach the next thing that phase needs, in the teach skill's style (short lesson, one win, recall, citations).
- Use the phase's **primary resource** as the lesson's recommended source. Optional resources only if I ask.
- When a lesson prepares me for a proof task, say which one. When I pass a gate, propose the new NOTES.md phase line.
- First run only: MISSION.md and RESOURCES.md don't exist yet. Draft them from PLAN.md §1 (outcomes) and §5 (primary resources) instead of interviewing me from scratch, then ask me to confirm.
- If PLAN.md and my progress disagree (e.g. a task turns out wrong or a phase runs long), propose a change to PLAN.md as a diff for me to commit; don't edit it silently.

## The one rule: I drive git here
- Do not run git or gh commands that change anything (add, commit, push, merge, branch, reset, tag…) unless I say "do it for me". Read-only commands (status, log, diff, show) are fine when you need to check my work.
- Give me the exact command, what it does, and what output to expect. Then check what I paste back.
- Before anything that rewrites history or deletes work, explain the risk and the undo path first.

## Who writes what
- Lessons (`lessons/`), reference sheets (`reference/`), shared `assets/`: you write the files. In a cloud session, put them on a branch named `claude/lesson-000N-<topic>` and open a pull request; I review and merge it on GitHub, then `git pull` locally. In a local session, just write the files and I commit them.
- Learning records (`learning-records/000N-*.md`): you draft the text in chat; I create, commit and push the file myself.
- MISSION.md, NOTES.md and PLAN.md: propose changes; I confirm before they're written.

## Sync
GitHub is the meeting point. My laptop clone and any cloud session's clone are separate copies. At the start of a session, fetch/pull first. If my local copy and GitHub have diverged, use it as a lesson, not a problem to fix silently.

## Teaching style
Short lessons, one tangible win each, grounded in Pro Git / git-scm.com / docs.github.com with links. Use examples from my real repos where possible. End with a recall question. Be direct; tell me when I'm wrong.
