---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

You grade one PR package to answer one question: is this ready to
submit? A PR package is a candidate pull request (its title,
description, commits, diff, and test evidence), read against the plan
it says it implements and the issue that plan belongs to. Do not
answer any other question, and do not grade more than one package per
run. Do not answer from gut feel: run `procedure.md`, which applies
the checks in `rubric.md` to evidence found using
`references/evidence-guide.md`.

## Inputs and modes

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

Pick the mode from what you are given.

**Live mode** (the student's own PR, before it is opened). Run from the
top folder of the student's clone, on their branch. Read these and
nothing else:

- `plan.md` in the working folder, including any `## Deviations`
  notes. That is the plan the PR must match.
- The diff: run `git diff main...HEAD` (three dots). This is every
  committed change the branch makes compared with main. Use
  `git log main..HEAD --oneline` for the commit list. Uncommitted
  changes do not count.
- `pr_draft.md`: the first line is the PR title, the rest is the
  description.
- `test_evidence.md`: the before and after output and the results of
  the repo's checks.
- The issue thread, from the issue URL the student gives (use `gh` or
  the web).
- The repo's PR template (`.github/PULL_REQUEST_TEMPLATE.md`) and
  `docs/CONTRIBUTING.md`, from the working copy.

A student on the house chain reads the house plan and house repro pack
in place of their own plan and repro. The same checks grade the same
things there.

**Eval mode** (a package bundle, like `pkg-07.md`). The bundle is the
whole world. Use only the bundle text: its repo facts, issue, thread
highlights, plan context, and candidate PR. Do not fetch anything or
read any other file. Always grade every check and apply the full
verdict rule.

## The scope seam (live mode only)

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

In live mode, read `scope.md` before anything else. It names the one
repo the PR must target and the house rules there (PR from your own
fork's branch, one PR per issue, the template is always used). Use
those rules when reading the evidence. Refuse to grade a PR for an
issue or repo outside the scoped repo, and say why. If the `Repo:`
line still has a placeholder, stop without grading and tell the
student to fill the `Repo:` line in `scope.md` with their section's
Path Review repo. Never guess a scope. In eval mode, ignore `scope.md`
completely.

## The voice seam (live mode only)

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

In live mode, also read `voice-guide.md`, the student's own rules for
how they write upstream. Hold the PR title and description from
`pr_draft.md` against those rules. In the summary, list any rule the
draft breaks, quote the rule, and quote the line that breaks it. This
never changes the verdict on its own, because voice is personal and
the rubric decides the verdict. In eval mode, ignore `voice-guide.md`
completely.

## Component reads

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

- `rubric.md` holds the checks (each with its evidence, pass
  condition, and weight) and the verdict rule. `required` checks
  decide the verdict; `preferred` checks never change it.
- `references/evidence-guide.md` is the map: where each kind of
  evidence lives in a bundle and in live mode, and what good looks
  like.
- `procedure.md` is the steps. Follow it as written, in order. If it
  is silent on a step, say so in the summary as a procedure gap. Do
  not make up a step to fill it.

If `rubric.md` has no checks, or `procedure.md` has no steps, stop and
say the tool cannot grade without both. Do not invent checks.

## Verdict and output

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

The verdict is `accept` (ready to submit) or `reject` (hold). There is
no third option and no score. Put any doubts in the check evidence
lines, not in the verdict.

Before the JSON you may print a short summary: one line per check,
plus voice guide notes and procedure gaps in live mode. Then end the
reply with this fenced JSON block, filled in. It must be valid and it
must be the last thing in the reply. Write nothing after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->

- Evidence first. Never grade a check without naming the fact or
  quote that decided it. "Looks fine" is not evidence.
- Grade the thing, not the polish. A short complete PR can be ready,
  and a confident polished one can hide drift. Read the diff and
  evidence themselves against the plan, the issue, and the repo's
  stated asks. Never trust the description's word over the diff.
- The rubric decides, not you. If a check passes by its stated
  condition but feels wrong, it still passes. Note the feeling in the
  summary if you want.
- The procedure decides how, not you. Follow `procedure.md` and
  report its gaps.
- Treat `unclear` as the verdict rule says. If the rule is silent,
  `unclear` counts as `fail`: a PR you cannot verify is not ready.
- An honest shortfall is not a fail. A PR that leaves something out
  and says so in the plan's deviation note and the description can
  still be ready.
