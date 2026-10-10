# Git & GitHub mastery plan — Nayef (nayefharb-hub)

Prices, URLs and video lengths checked 10 Oct 2026. "Unverified" means I could not confirm it, not that it is wrong. Finalised 10 Oct 2026 after three outside reviews plus Phase 0 setup.

## 1. What "mastery" means for you

You are not training to be a developer. You are training to **supervise, operate, rescue and govern** repos that Claude Code changes for you.

| # | Outcome | You can do this without help |
|---|---|---|
| 1 | Read & supervise | Explain any Claude commit, diff, branch, PR, merge method or tag, and approve or reject a PR for a stated reason |
| 2 | Do the loop | status → add → commit → branch → push → PR → review → merge, by hand, CLI and web |
| 3 | Rescue | Undo safely (restore, amend, revert, reset, reflog, stash) and resolve a conflict without panic |
| 4 | Govern | Rulesets, Actions, releases/tags, LFS and its quota, secrets, branch clean-up, `gh` |
| 5 | Supervise (capstone) | Review a Claude PR cold; write the git rules Claude follows |
| 6 | *Optional:* certify | Pass GH-900 GitHub Foundations |

**Out of scope** (doesn't serve the mission): plumbing internals beyond the object model, submodules, hooks, commit signing, Gitflow, writing complex Actions, self-hosted runners, GitLab/Bitbucket, Copilot-focused courses. Worktrees: recognise only (Claude Code may use them).

**PM analogies, and where they break**
- Commit = baseline. *Breaks:* local commits can be rewritten; an approved baseline can't.
- Branch = change request in progress. *Breaks:* it's only a movable pointer; costs nothing, holds no approval state.
- PR = review gate. Close match; rulesets make the gate mandatory.
- Tag = release milestone. Close match; a tag can be moved or deleted unless a ruleset protects it.

## 2. Plan at a glance

About **2 hours a week for ~12 weeks** covers outcomes 1–5. Each phase has one primary resource; everything in the Optional column is extra, not homework. The 12 weeks has almost no slack, and tasks 1.3 and 2.3 wait for Claude to open a real PR, so expect 13–14 weeks on the calendar. GH-900 adds 2–3 weeks.

| Phase | Weeks | Focus | Primary resource | Optional | Gate |
|---|---|---|---|---|---|
| 0 Setup | 0 (1 session) | `git config`, `gh auth login`, `git lg` alias, CLAUDE.md git rules, NOTES.md phase line | Pro Git 1.5–1.6 | VS Code Source Control or GitHub Desktop for reading diffs | `git lg` shows a graph in git-learning; Claude's next task prints its commands first |
| 1 Read | 1–3 | Commit, tree, branch, HEAD, remote-tracking branch; reading diffs, logs, PRs; 3 merge methods | Julia Evans zine, then Learn Git Branching *Introduction* + *Ramping Up* | MIT Missing Semester 2026 lecture; Pro Git ch. 2–3; Mahler video | Tasks 1.1–1.3 |
| 2 Do | 4–5 | The loop by hand; remotes; PR review | Pro Git 2.5 and 3.5, then GitHub Skills *Review pull requests* | Learn Git Branching *Remote*; *Git for Professionals* video | Tasks 2.1–2.3 |
| 3 Rescue | 6–7 | Undo ladder, conflicts, cherry-pick, rebase basics | Oh Shit, Git!?! and git-katas | GitHub Skills *Resolve merge conflicts*; Pro Git 7.3, 7.6, 7.7; ThePrimeagen on Master.dev (paid); *Advanced Git* video | Tasks 3.1–3.4 |
| 4 Govern | 8–11 | Rulesets, branch auto-delete, Actions, releases/tags, LFS, secrets, `gh` | GitHub Docs (linked in each task) | GitHub Skills *Hello GitHub Actions* (do it with 4.4), *Release-based workflow*, *Introduction to secret protection*, *Introduction to repository management*; GitHub for Beginners videos; Chacon talk | Tasks 4.1–4.5 |
| 5 Supervise | 12 | Cold PR review, CLAUDE.md rules, game day | Your own checklist | — | Graduation test |
| 6 Certify *(opt.)* | 13–15 | GH-900 domains you haven't covered | Microsoft Learn path + free practice assessment | aguidetocloud questions ($9) | Practice ≥ 80% |

Phases 1–3 are Git (local); Phase 4 is GitHub. Don't start Phase 4 before Phase 3: governance settings only make sense once you know what they prevent.

## 3. Weekly rhythm (Sun–Thu)

| Slot | Time | What | Where |
|---|---|---|---|
| Sun: Learn | 30–40 min | One lesson (read/watch the assigned item) + one recall question | `/teach` in git-learning, or the *Learning Git & GitHub* project chat on claude.ai |
| Tue: Practice | 30–40 min | You type the commands: one exercise | Your terminal, git-learning or Learn Git Branching |
| Thu: Apply + review | 30–40 min | One proof task on a real repo (read-only until Phase 4, except task 2.2) + 5 spaced-review questions; commit a learning record | Real repo + the project chat |
| Every Claude Code session | +5 min | Read the "git recap" and the PR's Files changed before merging | Work lane |

Rules: destructive commands (`reset --hard`, `push --force`, `branch -D`, `clean -f`, rebasing a shared branch) only in git-learning or a throwaway clone. Missed a week? Redo that week's review before moving on.

## 4. Proof-of-mastery tasks (your real repos)

Each task ends in a learning record in `git-learning/learning-records/`. Production repos stay **read-only until Phase 4**, with one deliberate exception: task 2.2, a one-line docs change that CI checks before merge.

### Phase 0: Setup
- ✅ `git config --global user.name/user.email`, `init.defaultBranch main`, `core.autocrlf true`, `alias.lg "log --graph --oneline --decorate --all"`. Git, Git LFS and `gh` confirmed installed, correct versions, signed in. Done — Windows, Git Bash.
- ✅ `user.email` set to the GitHub-generated noreply address (`<id>+nayefharb-hub@users.noreply.github.com`) rather than a personal inbox, so it's safe to appear in public-repo history.
- ✅ `nayefharb-hub/git-learning` created on GitHub (public) and cloned to `~/projects/git-learning`.
- **Finish the first hand-made commit.** In the cloned folder, add: Matt Pocock's teach skill under `.claude/skills/teach/` (copied from [mattpocock/skills](https://github.com/mattpocock/skills/tree/main/skills/productivity/teach)), this `PLAN.md`, the repo's `CLAUDE.md` (its rules govern every session here — read it before `/teach`), and an empty `NOTES.md`. `git add`, check with `git status` what's staged, then commit and push yourself.
- Add one line to `NOTES.md` and update it at every gate: `Current phase: 1 — next gate: task 1.1`.
- Optional: open a repo in VS Code's Source Control panel or GitHub Desktop. Use it to *read* diffs day to day; keep typing the commands in learning sessions.
- **Git narration, by PR.** In its next work session on each of Business-Case-Template, gantt-dashboard and Competency-Assessment-Platform, ask Claude to add this rule to that repo's own CLAUDE.md through a PR, and review the PR before merging — this keeps the read-only rule and gives you an early PR to review:
  > Before any git command, say in one line what it does and why. Never run destructive or history-rewriting commands (`reset --hard`, `push --force`, `branch -D`, rebase of a shared branch) without explaining the risk and asking first. End every session that touched git with a "git recap" under 10 lines: commands run, branch/PR involved, one thing worth learning.

### Phase 1: Read
- **1.1 Graph the two-branch repo.** Clone Business-Case-Template fresh without downloading its LFS files: `GIT_LFS_SKIP_SMUDGE=1 git clone <url>`. This task only needs history, and a normal clone pulls every Excel/Word file, which counts against the LFS bandwidth quota in 4.5. Only `main` exists locally; `kib-production` is there as the remote-tracking branch `origin/kib-production` (try `git log kib-production` first and read the error — that's the concept). Then run `git log --graph --oneline --decorate main origin/kib-production -20` and `git log --oneline main..origin/kib-production`. Explain in five sentences how the two relate, what a merge commit is, and where they last shared history (`git merge-base main origin/kib-production`). Is `v9.35-presample` annotated or lightweight (`git cat-file -t v9.35-presample`)?
- **1.2 Three merge methods, from your own PRs.** One squash-merged Competency PR (#25–#42), one merge-commit Business-Case PR (#20–#29), and gantt-dashboard PR #45. For each: how many commits landed on `main`, why, and what that means for `git revert` later. ([About pull request merges](https://docs.github.com/en/pull-requests/reference/pull-request-merges))
- **1.3 Supervisor review.** Before merging the next Claude PR, write a 5-line review (what changed, files, merge method, CI status, risk), then approve or request changes in the GitHub review UI.

### Phase 2: Do
- **2.1 Three PRs by hand in git-learning.** Branch → commit (conventional-commit message, as gantt-dashboard uses) → push → `gh pr create` → review your own diff → merge, using a different merge method each time. Compare `git lg` before and after.
- **2.2 One real change by hand (the deliberate exception).** In gantt-dashboard, fix one CHANGELOG or README line through a branch + PR, let `gates.yml` run, merge only when checks pass. Docs-only, one line, behind CI: that's why it's allowed before Phase 4.
- **2.3 Request changes from Claude.** Leave a line comment with "Request changes" on a Claude PR; after Claude pushes, verify with `git fetch` and `git diff origin/main...origin/<branch>`.

### Phase 3: Rescue (git-learning only)

The undo ladder — learn which rung you're on:

| Situation | Tool |
|---|---|
| Unstaged edit | `git restore <file>` |
| Staged edit | `git restore --staged <file>` |
| Last commit, not pushed | `git commit --amend` |
| Pushed / shared commit | `git revert` (or `gh pr revert <n>` for a whole PR) |
| Move a branch pointer | `git reset --soft / --mixed / --hard` |
| "I lost it" | `git reflog` |
| Committed on the wrong branch | `git switch -c`, `cherry-pick` |

- **3.1 Six-drill rescue kit.** Time each: (a) undo an unstaged edit, (b) fix the last commit message, (c) move a commit made on `main` to a new branch, (d) revert a commit from 5 commits ago, (e) recover a deleted branch via `reflog`, (f) stash, switch, pop. Target: under 2 min each, no lookup by round two.
- **3.2 Conflict, twice.** Create the same conflict and resolve it once on the CLI, once in GitHub's web editor. Write down what `<<<<<<<`, `=======`, `>>>>>>>` meant in your file. Extra reps: git-katas `merge-conflict`, `3-way-merge`, `rebase-branch`.
- **3.3 Revert a merged PR.** Use GitHub's **Revert** button (or `gh pr revert`) on a merged git-learning PR. Explain why revert, not reset, is the safe undo on a shared `main` ([git-revert](https://git-scm.com/docs/git-revert)).
- **3.4 Write `reference/rescue-card.md`** in git-learning: each mistake, the command, the undo, and the "never on main" rule. This becomes your 11 pm page.

### Phase 4: Govern (real repos, carefully)
- **4.1 Branch clean-up: Competency (~15 `claude/*` and `vercel/*` branches), then gantt-dashboard (4).** Squash-merged branches **don't show** in `git branch -r --merged` (their commits never reached `main` as-is). Check each with `gh pr list --state all --head <branch>`. Before deleting `claude/gstack-session-hook` or any `vercel/*` branch, confirm nothing still points at it (a hook in CLAUDE.md or settings, a Vercel preview or production branch setting). Before deleting anything, record the SHA (`git rev-parse origin/<branch>`) so a wrong delete is one command to undo: `git push origin <sha>:refs/heads/<branch>`. Delete merged/closed ones with `git push origin --delete <branch>`. Then [automatic deletion of head branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-the-automatic-deletion-of-branches): already on in Business-Case-Template; turn it on in gantt-dashboard; check Competency.
- **4.2 Ruleset on `main`, git-learning and Competency only.** Business-Case-Template and gantt-dashboard are private, and rulesets on private repos need GitHub Pro, Team or Enterprise ([About rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)) — Pro's exact monthly price isn't listed on GitHub's own pages (third parties say ~$4/mo, unconfirmed); check Settings → Billing and plans on your account for the real number. Rules: require a PR, block force pushes and deletion. **Don't require an approving review** — GitHub won't let you approve your own PR, so as a solo owner you'd lock yourself out. **Required status check, carefully:** you can only pick a check that has already run on the repo, and a required check that never runs blocks every merge. git-learning has no CI, so first add a one-job workflow and let it run on one PR (a small Actions warm-up before 4.4), or leave that rule off there. Competency has no Actions workflows; its only check is Vercel's deployment status, so require it only after you see it on a recent PR. Then ask Claude Code to push straight to `main` and record the rejection message. For the two private repos: write the rules you *would* set (incl. `kib-production`) into their CLAUDE.md and enforce them by review — or buy Pro and apply them.
- **4.3 Secrets audit (Competency is public).** Security tab → secret-scanning alerts; confirm push protection is on; `git log --all --oneline -- '.env*'` and `git log -p --all -S "<key prefix>"` for Supabase/Vercel prefixes; `.env*` in `.gitignore`, only `.env.example` tracked. If anything leaked: **rotate the key first**, then [remove sensitive data](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository). Rewriting history alone is not a fix.
- **4.4 Actions and releases.** Do GitHub Skills *Hello GitHub Actions* first (under 30 min). Then explain every trigger, job, permission and secret in gantt-dashboard's `gates.yml` and `release.yml` ([workflow syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)). Find a failed run with `gh run list` / `gh run view --log-failed`. Cut a release in git-learning with an annotated tag and `gh release create v0.1.0 --generate-notes`; check your v2.2.x tags against [SemVer](https://semver.org/) and the CHANGELOG against [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
- **4.5 LFS, Business-Case-Template.** `cat .gitattributes` and `git lfs ls-files` in the clone from task 1.1 (weeks will have passed, so run `git pull` there first). That clone skipped LFS downloads, so open one .xlsx: the small text pointer is what a client without LFS sees. Then run `git lfs pull --include="<that file>"` and open it again to see the real file. Check usage against the free **10 GiB storage / 10 GiB bandwidth**; over quota on a $0 budget, LFS is **blocked until the 1st of next month** ([Git LFS billing](https://docs.github.com/en/billing/concepts/product-billing/git-lfs)). Explain why two people editing one .xlsx can't auto-merge.

### Phase 5: Supervise (graduation)
- **Cold PR review checklist:** scope matches the ask? files touched? diff size sane? CI green? `.env`/secrets touched? LFS files only as pointers? any force-push or history rewrite? Write the review in the PR.
- Finalise the CLAUDE.md git rules from Phase 0 with what you've learned.
- **Game day:** ask Claude to script five broken states in a fresh sandbox (wrong branch, bad merge, hard-reset the wrong commit, committed secret, detached HEAD with work). Fix each in under 10 min with only `git` and `--help`.
- **Graduation test:** for one full week, merge nothing Claude made without a written review, and handle one real mishap yourself before asking Claude.

## 5. Resources

### 5a. Verdicts on your list

| Resource | URL check | Facts (Oct 2026) | Verdict |
|---|---|---|---|
| [Learn Git Branching](https://learngitbranching.js.org/) (Peter Cottle) | OK | Free, MIT, browser simulation. 7 sequences | **Use**, Phases 1–3. Skip *Advanced* sequences |
| [Oh My Git!](https://ohmygit.org/) (bleeptrack & blinry) | OK | Free desktop game, real git. Last release v0.6.5 (Jul 2022); README says "low-maintenance mode" | **Skip** (optional if you enjoy games). Overlaps Learn Git Branching |
| [GH-900 guide](https://www.aguidetocloud.com/guided/gh-900/) | OK | Unofficial personal site; 250 practice questions, 20 free, $9/yr. Its $49 exam price conflicts with other sources | **Optional**, Phase 6 only, after Microsoft's free practice assessment |
| [Boot.dev Learn Git](https://www.boot.dev/courses/learn-git) + Learn Git 2 (ThePrimeagen) | Your link redirects | Interactive; ~8 h + ~12 h. First chapters free, then **$59/mo or $399/yr** | **Optional.** Good but 20 h is more than you need. Don't buy it *and* Master.dev |
| [Julia Evans, How Git Works](https://wizardzines.com/zines/git/) | OK | Illustrated zine, **$12 PDF / $16 print+PDF** | **Use**, Phase 1. Fastest accurate mental model; one sitting |
| [ThePrimeagen, Everything You'll Need to Know About Git](https://master.dev/courses/everything-git/) | **Your URL is right**: Frontend Masters is now Master.dev; old links redirect | Video, 3 h 23 min (May 2024); conflicts chapter 55 min. **$39/mo or $390/yr**, no trial, 10-day refund | **Optional — best paid buy.** One month in Phase 3 |
| [Git Immersion](https://gitimmersion.com/) | OK | Free, 53 labs, needs Ruby set up | **Skip.** Same ground as Pro Git 2–3, plus setup friction |
| MIT Missing Semester: Version Control | Your 2020 link is **superseded** | [2026 edition](https://missing.csail.mit.edu/2026/version-control/); [lecture video](https://www.youtube.com/watch?v=9K8lB61dl3Y) 1 h 09 min (Feb 2026) + exercises | **Optional (2026)**, Phase 1. Exercises 2, 4, 8 |
| [Git In-Depth](https://master.dev/courses/git-in-depth/) (Nina Zakharenko) | Redirects to Master.dev | 3 h 27 min, Feb 2018 | **Skip.** Superseded by ThePrimeagen on the same subscription |
| [Git & GitHub Bootcamp](https://www.udemy.com/course/git-and-github-bootcamp/) (Colt Steele) | OK | 17 h, 190 lectures, updated Jan 2026, 4.8★. Price unverified (Udemy sales vary) | **Skip.** Too long and basic for you; no governance coverage |
| [Pro Git 2nd ed.](https://git-scm.com/book/en/v2) | OK | Free online/PDF/EPUB | **Use — reference spine.** Only ch. 1, 2, 3, 5.2, 7.1–7.7 |
| [Pro Git 3rd ed. preview](https://progit3.com/) | OK | In progress for Git 3.0; much is outline only, incl. a new "Git and Agents" chapter | **Skip for now.** Revisit that chapter when written — it's about your exact setup |
| [GitHub Skills](https://learn.github.com/skills) | skills.github.com **redirects** here | Free; template repos taught by a bot, 15–60 min each; catalogue now Copilot-heavy | **Use**, Phases 2–4: *Review pull requests*, *Resolve merge conflicts*, *Hello GitHub Actions*, *Release-based workflow*, *Introduction to secret protection*, *Introduction to repository management*. Skip *Introduction to GitHub* — you use GitHub daily. Keep copies **public** (private uses Actions minutes) |
| [Oh Shit, Git!?!](https://ohshitgit.com/) / [Dangit, Git!](https://dangitgit.com/) | Both OK | Free, 9 recipes | **Use**, Phase 3. Basis of your rescue card. It says `master`, and some recipes use `reset --hard` — practise in git-learning only |

### 5b. Added resources

**Video (free)**

| Video | Who | Length | Phase |
|---|---|---|---|
| [Git Explained in 100 Seconds](https://www.youtube.com/watch?v=hwP7WQkmECE) | Fireship | 2 min | 0–1 primer |
| [GitHub for Beginners playlist](https://www.youtube.com/playlist?list=PL0lo9MOBetEFcp4SCWinBdpml9B2U25-f) | GitHub (official) | 16 videos, 3–15 min each (2024–26) | 1, 4 — esp. *Actions* (8 min), *Security* (5 min), *Issues & Projects* (8 min) |
| [Introduction to Git: Core Concepts](https://www.youtube.com/watch?v=uR6G2v_WsRA) | David Mahler | 29 min | 1 (shorter alternative to MIT) |
| [Git for Professionals](https://www.youtube.com/watch?v=Uszj_k0DGsg) | freeCodeCamp / Tobias Günther | 41 min | 2 |
| [Git MERGE vs REBASE](https://www.youtube.com/watch?v=0chZFIZLR_0) | ByteByteGo | 5 min | 2–3 |
| [Advanced Git Tutorial](https://www.youtube.com/watch?v=qsTthZi23VE) | freeCodeCamp / Tobias Günther | 34 min | 3 (free alternative to Master.dev) |
| [So You Think You Know Git](https://www.youtube.com/watch?v=aolI_Rz0ZqY) (FOSDEM 2024) | Scott Chacon, Pro Git author | 47 min | 3–4 |
| *Skip:* Mosh "Git in 1 Hour", freeCodeCamp 2020 crash course | | ~1 h each | Beginner-level, nothing new for you |

**Hands-on and reading (free unless priced)**

| Resource | Phase | Use for |
|---|---|---|
| [git-katas](https://github.com/eficode-academy/git-katas) (Eficode, MIT) | 3 | Local drills: merge-conflict, 3-way-merge, rebase, reset. No reflog kata — drill that yourself |
| [Atlassian Git tutorials](https://www.atlassian.com/git/tutorials) | 3 | *Merging vs rebasing* and *Resetting, checking out & reverting* |
| Julia Evans free posts: [confusing terminology](https://jvns.ca/blog/2023/11/01/confusing-git-terminology/), [rebasing: what can go wrong](https://jvns.ca/blog/2023/11/06/rebasing-what-can-go-wrong-/) | 1, 3 | Seed for `reference/glossary.md` |
| [GitHub Docs](https://docs.github.com/): [GitHub flow](https://docs.github.com/en/get-started/using-github/github-flow), [PR reviews](https://docs.github.com/en/pull-requests/reference/pull-request-reviews), [rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets), [Actions](https://docs.github.com/en/actions/get-started/understand-github-actions), [releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases), [LFS](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage), [push protection](https://docs.github.com/en/code-security/concepts/secret-security/push-protection) | 2, 4 | Primary source for every Phase 4 task |
| [GitHub CLI manual](https://cli.github.com/manual/) | 2, 4 | `gh pr`, `gh run`, `gh release`, `gh ruleset`, `gh secret` |
| [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) | 2 | Decode gantt-dashboard's commit messages |
| *Learning Git* (Anna Skoulikari, O'Reilly 2023) | 1 (optional) | Visual print book, if you prefer it to the zine |

**Certification (Phase 6, optional)**
- [GH-900 GitHub Foundations](https://learn.microsoft.com/en-us/credentials/certifications/github-foundations/): 100 min, Pearson VUE, 7 domains. Official page says "price based on country"; third parties quote **~$99** — the earlier draft's $49 looks wrong. **Confirm at checkout in Kuwait.**
- Free: [study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/gh-900), [practice assessment](https://learn.microsoft.com/en-us/credentials/certifications/github-foundations/practice/assessment?assessment-type=practice&assessmentId=954809103) (take it *before* studying), [GitHub Foundations learning path](https://learn.microsoft.com/en-us/training/paths/github-foundations/).

### 5c. Budget

| Option | Cost | Contents |
|---|---|---|
| Free | $0 | Pro Git, Learn Git Branching, MIT 2026, GitHub Skills, git-katas, GitHub Docs, ohshitgit, the videos above |
| **Recommended** | **$12** | Free + Julia Evans zine |
| With video | $51 | + one month of Master.dev ($39) in Phase 3 |
| With cert | + ~$99 | GH-900 exam (+ $9 aguidetocloud questions, optional) |

## 6. How this fits your three lanes

- **Work lane** (Claude Code, real repos): Claude does the work, narrates, ends with a git recap; you review before merging (1.3). From Phase 4 you make governance changes yourself.
- **Learn lane** (`/teach` in git-learning): Sunday lesson for the phase named in NOTES.md, you type every command, learning record per insight.
- **Think lane** (the *Learning Git & GitHub* project chat on claude.ai): debriefs, Thursday spaced review, "what did Claude do here?".

**First three sessions:** (1) Phase 0 setup + the Fireship video; (2) the Julia Evans zine + Learn Git Branching *Introduction*; (3) task 1.1 on Business-Case-Template.

## Unverified items
- GH-900 exact price in Kuwait (country-priced).
- Udemy price for the Colt Steele course.
- GitHub Pro's exact monthly price — official pages don't list it; third-party sources say ~$4/mo. Check Settings → Billing and plans on your own account before relying on this.
