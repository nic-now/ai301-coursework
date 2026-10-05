# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

Where it lives: the environment section at the top of the repro report. In the eval bundle, look for the environment or setup section of the repro report. In live mode, look at the top of the draft comment or any template field labeled environment or setup.

What good looks like: the report names the exact tool or language version (like "Python 3.11" or "Node 18.2") and the OS (like "macOS 14" or "Windows 11"). Vague entries like "latest" or just "Mac" are not enough.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

Where it lives: the steps section of the repro report. In the eval bundle, look for the numbered list in the repro report body. In live mode, look at the body of the draft comment.

What good looks like: the steps go in order from a clear starting point to where the bug appears. Someone who has never seen the project could follow them without guessing a command, file, or value.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

Where it lives: any output, error message, log excerpt, or screenshot attached to or pasted in the report. In the eval bundle, look for the artifacts section or any quoted output in the repro report body. In live mode, look for pasted output in the draft.

What good looks like: the artifact shows the same error or unexpected behavior the original issue describes, not something similar but different. A log showing a different error than what the issue names is not a match.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

Where it lives: the outcome or result section of the repro report. In the eval bundle, look for where the student states what they observed. In live mode, look at the conclusion of the draft.

What good looks like: the report says exactly what happened, including if the bug could not be reproduced. A "cannot reproduce" with a clear description of what was seen instead is a pass. A report that claims reproduction but shows no artifact, or shows a different behavior, is a fail.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

Where it lives: the claim comment the student plans to post. In the eval bundle, look for the claim comment section. In live mode, look at the draft comment and any CONTRIBUTING.md or issue template the repo uses.

What good looks like: the comment clearly states what the student found (reproduced or not), does not make promises they cannot keep, and follows any template or AI disclosure requirement the repo asks for. Silence on AI use is only fine if the repo does not require disclosure.
