# Phase 0 setup: first commit and push

Set up git-learning's working tree (teach skill, PLAN.md, CLAUDE.md, NOTES.md) and completed two full add→commit→push cycles by hand. Two Windows-specific gotchas worth remembering: NTFS is case-insensitive, so renaming a file to fix only its letter-casing (e.g. plan.md → PLAN.md) needs an intermediate name or it silently no-ops; and core.autocrlf true converts LF→CRLF in the working copy automatically, so that warning on git add is expected, not an error.

## Evidence
Pushed commits 34f1677 and the one before it to nayefharb-hub/git-learning, main branch, entirely by hand — no commands run by Claude.