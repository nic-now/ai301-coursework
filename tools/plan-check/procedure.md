# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the issue context and repro evidence first. Note what behavior the repro evidence pins down: what triggers the bug and what the output shows. This is the baseline all other checks compare against.
2. Read the full candidate plan. Note the stated cause, every file name mentioned, and the test plan.
3. Read the plan comment last. Note whether it addresses the thread and follows any repo conventions.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

- Diagnosis: pull the cause statement from anywhere in the plan. Pull the bug behavior from the repro evidence. Record both to compare.
- Scope: pull every file name and description of what will change from the plan.
- Focused: use the cause from the plan and the root behavior from the repro evidence side by side.
- Test: pull the test steps or observable check from the plan. Pull the repro steps from the repro evidence to compare.
- Conventions: pull the plan comment text. Pull the repo's contribution policy and any templates from the repo-facts block.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

Run checks in this order: diagnosis → focused → scope → test → conventions. Use the notes from evidence gathering; do not re-read the full package for each check.

For each check:
1. Apply the pass condition from the rubric to the gathered evidence.
2. If the evidence needed for a check is genuinely absent (no cause stated, no files named, no test described), grade it unclear.
3. Grade only what the package contains, not what you think the author meant.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. If every required check passed → verdict is accept (ready).
2. If any required check failed or is unclear → verdict is reject (hold).
3. In the output, quote the name of the check that caused the hold and the one-line evidence that decided it.
