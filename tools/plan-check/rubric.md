# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis | The plan's stated cause, read against the repro evidence in the issue and the reproduction | The plan names the root cause and it is consistent with what the repro evidence shows; ignoring or contradicting the repro evidence fails | required |
| scope | The list of files and changes stated anywhere in the plan | The plan names the specific files it will touch and what it will change in each; vague references without file names fail; changes outside the bug's scope fail | required |
| focused | The plan's approach, read against the repro evidence | The plan targets the root cause the evidence points at, not just the visible symptom; a fix that only hides the symptom while the repro evidence shows a deeper cause fails | required |
| test | The test section or test plan anywhere in the plan, read against the repro steps | The test describes observable before/after behavior a stranger could verify; stating expected behavior without a runnable check or concrete output fails | required |
| conventions | The plan comment text, read against the issue thread and any repo templates or CONTRIBUTING.md | The comment follows the repo's stated conventions and responds to anything the thread has asked; boilerplate that ignores the thread fails | required |


## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes/ready; fail/hold if unclear (?) or not all required check passed; preferred checks don't change verdict.

<!-- Diagnosis (required): look in Candidate’s plan section; pass if the plan says what causes the bug and explains how to reproduce it
Scope (required): Look in scope section; l pass if the plan specifies and names all the files the changes are going to occur in and what exactly is going to be changed
Test (required): look in the testing section; pass if there exists an automated test which checks the bugs and makes sure the fixes works properly, and it can be reproduced/verified easily

Verdict rule:
Ready if all the checks pass

Hold if any check fails or if check is unsure (?) -->

<!-- Our procedure
1. What to read first
which parts of the file, in what order
It would first read the Candidate’s Plan section, Diagnosis section in the calib3.md file, and proceed to the Scope section, going lastly to the Test plan section

2. How to gather the evidence
what to pull from each part of the file, and what to compare it with
Execute the test plan, gather the output, and compare the output to the evidence from the “Repro Evidence” sub-section of the Issue section..

3. How to grade each check
what to do for each check, including when the evidence is missing
Diagnosis: first, look into the Candidate's plan for information on what exactly causes the bug and how to reproduce. If either or both of these issues are missing, then this check would be F
Scope: looks into the candidate plan’s scope section in the same file, for the exact file name the specified changes are going to occur.
Test: look into the Candidate plan in the file and review how they have completed the test and make sure they are automated.

4. How to reach the verdict
If we see any grade checks fail, or a check is unsure, then we claim our verdict is on hold; else, our verdict is ready.


Phase 3: test and fix
Phase 3 · As a Group · 15 minutes · calib-01
Now test your own rubric the same way. Follow your own procedure, step by step, to grade calib-01 with your rubric. One person reads each step aloud; do only what it says.
Then fill in the boxes below, in order.
Last 5 minutes: fix “Our rubric” and “Our procedure” above, and list the changes below.

Grades for calib-01
one line per check from YOUR rubric (Phase 2): its name, P / F / ?, and why
Diagnosis: P, because it still specifies the cause of the bug and repro details
Scope: P
Test: F, because in the candidate plan it talks about using the repro steps above

Verdict
ready or hold
hold

Compare with the correct verdict
the correct verdict is ready. If your rubric said hold, name the check that rejected it and what calib-01 does instead. Is the check asking for the wrong thing?
The test check rejected it and the calib-01 instead just talked about using the repro steps, and didn’t 

What we changed
one line per change: what you changed, and whether it’s in the rubric or the procedure
Changed the test 
Diagnosis: changed wording so its not too specific (looking for a specific diagnosis section)
Test: changed due to being a requirement of automation; fails the test fixes would be removing the automation test.


Phase 4: debrief
Phase 4 · As a Group · 5 minutes
Agree on one answer and write it below.

What would Claude have gotten wrong without your procedure?
It would have looked for specific sections (e.g. diagnosis, scope, etc.) and might have even hallucinated them if they weren’t present. -->





