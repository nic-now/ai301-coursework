# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

1. Read the repo facts first (eval) or the PR template and
   `docs/CONTRIBUTING.md` (live). Write down every required section,
   checklist item, and whether there is an AI-use policy.
2. Read the issue and thread. Note the repro steps and any maintainer
   direction or question.
3. Read the plan (plan context block, or `plan.md` with its
   deviations). Write down: the files and changes it promises, what it
   says is not in scope, any deferral note, and its test plan cases.
4. Read the diff and commit list next, before the description. List
   every file and hunk and what it does. The plan comes before the diff
   so you can compare, and the diff comes before the description so the
   description's wording does not shape what you see in the diff.
5. Read the test evidence. Note each command or repro shown and its
   before and after output.
6. Read the title and description last. Note each claim it makes about
   what the PR does.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

Build these side by side lists from your notes:

- plan-match: put the diff's hunk list next to the plan's promised
  changes. Mark each hunk "in plan", "in deviation note", or "not in
  plan". Mark each planned step "in diff", "deferred with note", or
  "missing".
- honest-description: put each description claim next to the diff.
  Mark each claim "in diff" or "not in diff". Also note any hunk
  marked "not in plan" that the description does not mention.
- decisive-test: put the plan's test plan cases next to the test
  evidence. For each case, record whether it is shown with real
  before and after output, and whether it runs the path the fix
  changes (not a control).
- repo-checks: list any suite or check the plan or template names.
  Record whether the evidence shows it ran and its result.
- clean-diff: scan every added line for debug prints, commented-out
  code, dead functions, and churn (lines changed only for spacing,
  ordering, or imports the fix does not need). Also note commits named
  like "wip" or "debugging".
- template-and-disclosure: put the required sections and checklist
  items from step 1 next to the description and diff. Mark each
  "filled" or "missing". If there is an AI policy, record whether the
  description has a disclosure.
- thread-engaged: put each maintainer ask from step 2 next to the
  description.

In live mode, get these from the files listed in SKILL.md: `plan.md`,
`git diff main...HEAD`, `pr_draft.md`, `test_evidence.md`, the issue
thread, the PR template, and `docs/CONTRIBUTING.md`.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

Run checks in rubric order: plan-match, honest-description,
decisive-test, repo-checks, clean-diff, template-and-disclosure,
thread-engaged. Grade each from its list above; do not re-read the
whole package unless the list is missing something.

For each check:
1. Apply the rubric's pass condition to the list.
2. A "not in plan", "missing", "not in diff", or debris mark fails
   the check, unless it is openly disclosed in a deviation note or the
   description (for plan-match, honest-description, and decisive-test).
3. If the evidence the check needs is not in the package at all, grade
   it unclear.
4. Write one evidence line: the hunk, quote, or missing item that
   decided it.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->

1. If every required check passed, the verdict is accept.
2. If any required check failed or is unclear, the verdict is reject.
3. Preferred checks never change the verdict.
4. In the summary, name the deciding check: the first failing (or
   unclear) required check in rubric order, with its evidence line.
5. End with the JSON block from SKILL.md, one entry per check in rubric
   order.
