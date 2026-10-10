# Mission: Git & GitHub

## Why
Claude Code does the git/GitHub work in my real repos (Business-Case-Template, gantt-dashboard, Competency-Assessment-Platform). I'm a PMO lead, not a developer. I need to supervise what it does, review it, and rescue things when it goes wrong.

## Success looks like
- Explain any Claude commit, diff, branch, PR, merge method or tag, and approve or reject a PR for a stated reason
- Run the everyday loop by hand: status → add → commit → branch → push → PR → review → merge
- Undo mistakes safely (restore, amend, revert, reset, reflog, stash) and resolve a conflict without panic
- Govern the repos: rulesets, Actions, releases/tags, LFS quota, secrets, branch clean-up, `gh`
- Review a Claude PR cold and write the git rules Claude follows (graduation, Phase 5)

## Constraints
- About 2 hours a week over ~12 weeks (13–14 on the calendar)
- Windows, Git Bash, Bash-syntax commands only
- I type every git command; Claude doesn't change anything unless I say "do it for me"
- Real repos are read-only until Phase 4, except task 2.2. Destructive drills only in git-learning.
- Free resources first. Recommended spend is $12 (the Julia Evans zine).

## Out of scope
- Git plumbing beyond the object model, submodules, hooks, commit signing, Gitflow
- Writing complex Actions, self-hosted runners, GitLab/Bitbucket, Copilot courses
- Worktrees: recognise only
- Becoming a developer
