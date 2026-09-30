# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

[Your GitHub username, exactly as it appears on your profile — no `@`, no profile URL. Your
comments upstream are identified by this name.]
nic-now
---

## Posted upstream

**Claim comment**

[Link to the comment where you claimed the issue. Use the comment's own permalink, not the
issue page on its own. **Then paste the text of that comment underneath the link** — the
pasted text is what this field is graded on, so copy across what you actually posted.]

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->
First run: 15/20
Run after editing rubric: 15/20 (with different accepted/rejected packages)
Last run: 20/20

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->

pkg-16: rubric said accept, gold said reject. The report shows the right crash, but uses pandas 1.5.3 when the issue was confirmed on latest (3.0.5) and main. The version gap is never mentioned. My check was only looking at whether the artifact matched the crash, not whether the environment matched the issue's target.

**Check rationale**

<!-- [Quote one check from the `rubric.md` you uploaded to `tools/repro-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->

"| matches-issue | Any output, log excerpt, error message, or screenshot in the report, read against the error or behavior described in the original issue | Either: the artifact shows the same bug the issue describes on an environment matching the issue's target version (or deviation is explicitly stated), OR the report honestly states cannot-reproduce with real evidence of what was tried and names what differed; fail if reproduction is claimed but the artifact shows a different bug, or if the version silently mismatches the issue's stated target without acknowledgment. | required |"

I rewrote this twice:
- First version failed honest cannot-reproduce packages (pkg-09, pkg-10) because no bug was shown
- Loosened it to allow cannot-reproduce with evidence
- Added the silent version mismatch condition to still catch pkg-16

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

Loosening matches-issue to allow cannot-reproduce risked flipping wrong-target packages. I re-ran pkg-02, pkg-08, and pkg-17 as canaries after the change and they all kept as reject so nothing broke.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
