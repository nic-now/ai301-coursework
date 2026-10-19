# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

- Practice submission: the "Plan context" block (the "Plan:" text, its
  "Files:" list, "Not in scope", and any deferral or known limit note),
  then the "Diff" and "Description" under "Candidate PR".
- My PR: `plan.md` (scope, files, and `## Deviations`), the output of
  `git diff main...HEAD`, and the description in `pr_draft.md`.
- Good looks like: every hunk in the diff traces to a plan step or a
  deviation note, every plan step is in the diff or openly deferred,
  and every claim in the description is in the diff. Drift looks like
  an extra option, rename, or rewrite the plan never named, or a
  promised step (like a docs update) missing while the description
  says it is done.

## Test evidence (harness category: not-tested)

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

- Practice submission: "Test evidence" under "Candidate PR", read
  against the "Test plan:" line and "Repro evidence" in the plan
  context, and the issue's steps.
- My PR: `test_evidence.md` (before on main, after on my branch, and
  the output of `make test-unit`, `make test-integration`,
  `make lint`, `make typecheck`), read against the test plan in
  `plan.md`.
- Good looks like: the same repro the plan names is re-run on the
  changed path, with real before and after output, every case in the
  test plan is shown, and the repo's checks are named with their
  results. A failing check reported honestly with the reason still
  counts. "Works on my machine" or "tests pass" with nothing shown
  does not.

## Diff quality (harness category: unreviewable)

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

- Practice submission: the "Diff" and "Commits" under "Candidate PR".
- My PR: `git diff main...HEAD` and `git log main..HEAD --oneline`.
  Before pushing, `git diff main...HEAD --stat` should list only the
  files the fix changes.
- Good looks like: only the fix and its tests, with commit messages
  that say what changed. Debris looks like `print` or `eprintln` debug
  lines, commented-out old attempts, unused functions, re-indented or
  reordered lines the fix does not need, and commits named "wip" or
  "misc cleanups".

## Standards and comms (harness category: standards-wall)

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->

- Practice submission: the "Repo facts" block ("pull requests:" for
  template asks, "contribution policy" for any AI policy) and "Thread
  highlights", read against the "Description" and "Diff".
- My PR: `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`
  in the Path Review repo, the issue thread on GitHub, and the
  description in `pr_draft.md`.
- Good looks like: every section the template asks for has real
  content (Summary, Issue with "Closes #", Changes, Testing with only
  true boxes ticked, Screenshots or "N/A" with a reason, Notes for
  Reviewers), any required changelog or checklist is done, and an AI
  use disclosure is there when the repo asks for one (Path Review
  always does). Any maintainer ask in the thread is answered.
