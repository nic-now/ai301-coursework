# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer is active | `"last 5 default-branch commits"` and `"maintainer first-response sample"` under Repo facts (eval bundle); on GitHub, front-page commit history and Issues tab sorted by recently updated | At least one of the last 5 default-branch commits is by a human (username not ending in `[bot]`) within 35 days of the capture date, OR a maintainer (Owner/Member/Collaborator) has responded to any sampled issue within 60 days | required |
| Repo is active | `"last push to any branch"` and `"archived:"` under repo facts (eval bundle); on GitHub, front page newest commit date and Releases sidebar | Last push to any branch is within 60 days of the capture date and repo is not archived | required |
| Scope fits newcomer | Issue body and comment thread (look for umbrella/tracking issue markers) (list of sub-items meant to be split), ongoing design debate with no settled direction, or a maintainer comment saying the fix touches core internals | Issue describes a single bounded task (not a tracking/umbrella issue), no maintainer comment says the fix requires touching core internals, and no unresolved design debate in the thread blocks starting work | required |
| Issue is free | `"this issue: assignees:"` and `"linked PRs:"` with state per PR under repo facts (eval bundle); comment thread for claim phrases ("I'll take this", "working on this") and whether a maintainer replied | Assignees box is empty, no open linked PR exists, and no unanswered claim comment appears within the last 30 days | required |
| No AI contribution ban | `"contribution policy"` line under Repo facts (eval bundle); on GitHub, `CONTRIBUTING.md` in repo root or `.github/`, plus any `AI_POLICY.md` or `AI_USAGE_POLICY.md` | CONTRIBUTING.md and any AI policy file contain no outright ban on AI-generated or AI-assisted contributions; silence is a pass; conditions such as disclosure or review requirements count as pass | required |
| Proper issue description | Issue body | Issue body describes the bug, feature, or task clearly enough to begin work without asking the maintainer for clarification (a minimal reproduction, acceptance criteria, or a clear description of the desired behavior) | preferred |

## Verdict rule
<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
Accept if every required check passes. Preferred checks never change the verdict; they only rank accepted issues against each other. Unclear on any required check counts as fail (reject).
