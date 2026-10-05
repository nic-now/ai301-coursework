# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56


**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

---
  1. #56 (top pick) — Tier-1, labeled "good first issue," single-method fix in a Python RAG/chunking component (AI/ML
  adjacent), minimal codebase context required, clear reproduction snippet. Best match for limited time + preference for
  simple bugs.

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

``` json
---
  Issue #56 — "Structural chunker silently drops documents that contain no headings"

  ┌────────────────────────┬───────┬─────────────────────────────────────────────────────────────────────────────────────┐
  │         Check          │ Grade │                                      Evidence                                       │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ Maintainer is active   │ pass  │ Aburke225 committed Sept 16, 2026 (7 days ago), human author, within 35-day window  │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ Repo is active         │ pass  │ Last push Sept 16, 2026; repo not archived                                          │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ Scope fits newcomer    │ pass  │ Single bounded task: fix StructuralChunker.chunk() to handle heading-free docs;     │
  │                        │       │ labeled "good first issue" / tier-1; no tracking markers, no design debate          │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ Issue is free          │ pass  │ Assignees: none; linked PRs: none; no claim comments visible                        │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ No AI contribution ban │ pass  │ No CONTRIBUTING.md or AI policy files; silence passes                               │
  ├────────────────────────┼───────┼─────────────────────────────────────────────────────────────────────────────────────┤
  │ Proper issue           │       │ Includes runnable Python snippet reproducing the exact failure and names the        │
  │ description            │ pass  │ failing test                                                                        │
  │ (preferred)            │       │                                                                                     │
  └────────────────────────┴───────┴─────────────────────────────────────────────────────────────────────────────────────┘

  Verdict: ACCEPT

  ---
---
  [
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56",
      "checks": [
        {"name": "Maintainer is active", "grade": "pass", "evidence": "Aburke225 committed Sept 16, 2026 (7 days ago), human,
   within 35-day window"},
        {"name": "Repo is active", "grade": "pass", "evidence": "Last push Sept 16, 2026; repo not archived"},
        {"name": "Scope fits newcomer", "grade": "pass", "evidence": "Single bounded task: fix StructuralChunker.chunk() for
  heading-free docs; labeled tier-1/good first issue; no tracking markers or design debate"},
        {"name": "Issue is free", "grade": "pass", "evidence": "Assignees: none; linked PRs: none; no claim comments"},
        {"name": "No AI contribution ban", "grade": "pass", "evidence": "No CONTRIBUTING.md or AI policy files found; silence
   passes"},
        {"name": "Proper issue description", "grade": "pass", "evidence": "Runnable Python snippet reproducing exact failure,
   names failing test test_document_with_no_headings"}
      ],
      "verdict": "accept"
    },
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/55",
      "checks": [
        {"name": "Maintainer is active", "grade": "pass", "evidence": "Aburke225 committed Sept 16, 2026 (7 days ago), human,
   within 35-day window"},
        {"name": "Repo is active", "grade": "pass", "evidence": "Last push Sept 16, 2026; repo not archived"},
        {"name": "Scope fits newcomer", "grade": "pass", "evidence": "Single bounded task: fix
  _detect_languages/_detect_tools/_detect_databases in skill_extractor.py; no umbrella markers or design debate"},
        {"name": "Issue is free", "grade": "pass", "evidence": "Assignees: none; linked PRs: none; no claim comments"},
        {"name": "No AI contribution ban", "grade": "pass", "evidence": "No CONTRIBUTING.md or AI policy files found; silence
   passes"},
        {"name": "Proper issue description", "grade": "pass", "evidence": "Names exact file, functions, and failing xfailed
  tests with pytest command to reproduce"}
      ],
      "verdict": "accept"
    },
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/67",
      "checks": [
        {"name": "Maintainer is active", "grade": "pass", "evidence": "Aburke225 committed Sept 16, 2026 (7 days ago), human,
   within 35-day window"},
        {"name": "Repo is active", "grade": "pass", "evidence": "Last push Sept 16, 2026; repo not archived"},
        {"name": "Scope fits newcomer", "grade": "pass", "evidence": "Single bounded task: add ownership check in
  create_review(); no umbrella markers, no core-internals comment, no design debate"},
        {"name": "Issue is free", "grade": "pass", "evidence": "Assignees: none; linked PRs: none; no claim comments"},
        {"name": "No AI contribution ban", "grade": "pass", "evidence": "No CONTRIBUTING.md or AI policy files found; silence
   passes"},
        {"name": "Proper issue description", "grade": "pass", "evidence": "Describes specific endpoint, function, impact, and
   example exploit request; clear enough to begin work without asking maintainer"}
      ],
      "verdict": "accept"
    }
  ]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

First run: 10/20
Second run: 18/20

**Issue analysis**

<!-- [One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.] -->

id: issue-15
rubric=accept
gold=reject
The issue had two closed linked PRs and many claim comments, but all were old, the most recent visible claim was from 2024, so outside the 30 day window. The rubric's issue-is-free check only looks for open PRs and recent unanswered claims, so it passed. Gold rejected it because the long history of abandoned attempts signals the issue is harder or more stuck than it looks, which the rubric had no check for.

**Check rationale**

<!-- [One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.] -->

"| Issue is free | `"this issue: assignees:"` and `"linked PRs:"` with state per PR under repo facts (eval bundle); comment thread for claim phrases ("I'll take this", "working on this") and whether a maintainer replied | Assignees box is empty, no open linked PR exists, and no unanswered claim comment appears within the last 30 days | required |"

The 30 day window for claim comments is a judgment call. Shorter would reject issues where an old comment is just noise; longer would incorrectly block issues that have been sitting untouched for months. I set it at 30 days to balance both

**Trade-offs**

<!-- [What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

The check accepts issues with a pattern of repeated failed attempts, like issue-15, as long as no open PR or recent claim exists. It cannot detect that multiple people have tried and abandoned the same issue, which is a real signal that something is wrong with it.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

<!-- [Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.] -->

1. The issue is interesting to me because it deals in some sorts with RAG (though its more data processing), which could help me learn more about things to consider when doing my own version. Also, it is listed as tier-1, and as a good first issue, and it's a parsing-related issue, thus I think I can address it in time.
2. The skill correctly identified the issue was free (no assignee, no open PR), the repo was active, and the scope was a single bounded fix in one method. What the rubric could not weigh: whether the codebase was approachable for me specifically (Python, small component, no framework knowledge needed), and whether the bug was simple enough to trace without deep context of the full system.
3. For claiming, I believe it shouldn't be too hard, given that reproduction instructions are ~clear, as well as instructions on repo.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
