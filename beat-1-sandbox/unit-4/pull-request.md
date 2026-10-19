# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

<!-- [Link to the pull request you opened. It must be the pull request's own page on the Path
Review repo, not your fork's branch page.] -->
https://github.com/nic-now/pathreview-ai301-fa26-s1/pull/1#issue-5918710854

**Branch**

<!-- [The name of the branch the pull request comes from, exactly as it appears in your fork.
The naming shape is a type prefix, then the issue number, then a short description. **The
issue number in the branch name must be the number of the issue the pull request fixes** —
a name carrying any other number does not satisfy this field.] -->
fix/56-structural-chunker-no-headings

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->
Run: 20/20

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->
- pkg-17
- My rubtic: reject 
- Gold label: reject
The gold note says "the plan promises a dev warning AND a docs update; the diff contains only the warning while the description claims the docs 'now document the limitation'". My honest-description check caught it because it compares what the description claims to what the diff really has, and the docs change was not in the diff.

**Check rationale**

<!-- [Quote one check from the `rubric.md` you uploaded to `tools/pr-precheck/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->
| honest-description | The PR title and description's claims, read against the diff | Everything the description says the PR does is actually in the diff, and it does not hide anything big the diff does. Claims like "exactly as planned" or "no other changes" over a diff that does more fail. Claiming docs, tests, or a fix that the diff does not contain fails. | required |

I wrote it this way so the check judges the diff, not how nice the description looks. It is required because a description that lies about the diff is the main way silent drift gets through.

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->
Nothing changed after my first run. It scored 20/20 with every category matched, so I did not revise any file or loosen any check, and I did not need canaries. A case it will miss: a package where the description is honest but the diff has small debris that the clean-diff check does not see.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
