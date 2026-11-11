---
name: pr-reviewer
description: >-
  Use this skill when the user asks to review a pull request, a diff, a branch,
  or staged changes. Produces a structured review with ranked findings and a
  merge recommendation.
---

# PR Reviewer

Review code changes the way a careful senior engineer would.

## Steps

1. Identify the change set. Prefer, in order: a PR number the user gave
   (`gh pr diff <n>`), a branch (`git diff main...<branch>`), staged changes
   (`git diff --cached`), or the working tree (`git diff`).
2. Read every changed file in full, not only the hunks, so you understand
   the surrounding logic.
3. Check, in this order: correctness (logic, edge cases, error handling),
   security (injection, secrets, auth, unsafe deserialisation), concurrency,
   performance on hot paths, tests (missing or weakened), and style only
   where it hides a bug.
4. Run the project's test command if one is obvious from the repo and the
   change is small enough to test quickly.

## Output format

```
## Summary
One paragraph: what the change does and whether it is safe to merge.

## Findings (highest severity first)
1. [BLOCKER|MAJOR|MINOR] path/file.ext:line — what is wrong, why it matters, how to fix.

## Recommendation
Merge | Merge after fixes | Do not merge — one sentence why.
```

## Rules

- Every finding cites a file and line. No finding without a concrete fix.
- Do not restate the diff. Do not praise. Keep the summary under 120 words.
- If the change set is empty or cannot be determined, say so and stop.
