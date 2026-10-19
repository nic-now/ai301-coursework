# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-match | The diff's changed files and hunks, read against the plan's scope, its "not in scope" list, and its deviation notes | Every change in the diff is something the plan (or a deviation note) asks for, and every step the plan promises is in the diff or is openly deferred in a deviation note or the description. An extra feature, option, rename, or rewrite the plan does not mention fails. A planned step that is missing with no note fails. | required |
| honest-description | The PR title and description's claims, read against the diff | Everything the description says the PR does is actually in the diff, and it does not hide anything big the diff does. Claims like "exactly as planned" or "no other changes" over a diff that does more fail. Claiming docs, tests, or a fix that the diff does not contain fails. | required |
| decisive-test | The test evidence, read against the plan's test plan and the issue's repro steps | The evidence re-runs the plan's repro on the path the fix changes and shows an observable before and after (real output, not just "works now"). Every repro case the test plan names is shown, or its absence is openly explained. "Tested locally", "works on my machine", "tests pass" with nothing shown, or evidence that only runs a control or an unchanged path fails. | required |
| repo-checks | The test evidence, read against the suite or checks named in the plan's test plan or the repo's template | If the plan or the repo names a suite or check to run, the evidence names it and shows its result. A failing or skipped check reported honestly, with the reason, passes. If nothing is named anywhere, pass. | required |
| clean-diff | The unified diff and the commit list | The diff holds only the change and its tests. Any of these fails: debug prints or logging left in, commented-out code, dead or unused functions, import or formatting churn in lines the fix does not need, unrelated hunks. Comments that explain the fix are fine and do not count as commented-out code. | required |
| template-and-disclosure | The repo facts block (PR template asks, contributing guide, AI policy), read against the PR description and diff | Every section or checklist item the repo's template or guide says is required has real content (for example a "closes #" line, a checklist, a changelog or whatsnew entry in the diff). If the repo states an AI-use policy, the description has an AI-use disclosure. If the repo asks for nothing, pass. | required |
| thread-engaged | The thread highlights, read against the description | If a maintainer gave direction or asked a question in the thread, the description follows it or answers it. If the thread is empty, pass. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes. Reject if any required check
fails or is unclear, because a PR we cannot verify from the package is
not ready. Preferred checks never change the verdict. An honest,
disclosed shortfall (noted in the plan's deviations or the
description) is not a fail by itself.
