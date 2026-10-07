# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

<!-- [Your GitHub username, exactly as it appears on your profile - no @, no
profile URL. Your comment upstream is identified by this name, and it is
the only thing that ties it to you. Several students may plan the same
house issue, so this is what keeps their comments off your score and
yours off theirs.] -->
nic-now

**Plan comment**

<!-- [Link to the comment where you posted your plan on the issue. Use the comment's own
permalink. **Then paste the text of that comment underneath the link** — the pasted text is
what this field is graded on, so copy across what you actually posted.] -->

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/56#issuecomment-6031036799

**Diagnosis**
My repro showed the issue snippet prints `0`, and the test fails with:
```
E       assert 0 >= 1
E        +  where 0 = len([])
```
 `chunk()` returns an empty list for a document with no headings. In `structural_chunker.py`, `_extract_sections()` only keeps text that comes after a heading. With no headings, it finds no sections, so `chunk()` has nothing to return.

**What I'll change:**
- `ingestion/chunking/structural_chunker.py`: in `chunk()`, if no sections are found, use the whole document as one section.
- `tests/unit/test_structural_chunker.py`: remove the `xfail` marker from `test_document_with_no_headings` so it runs as a normal test.
**What I won't change:**
- `_extract_sections()` and how documents with headings are chunked
- Text before the first heading in documents that do have headings (that is a separate bug)

**Approach:**
Add a small fallback in `chunk()` instead of rewriting the section logic. Long documents with no headings will still get split by the semantic chunker like other large sections.

**Test Plan:**
Run before and after the fix:
1. `.venv\Scripts\python -m pytest tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings`
   Before (add `--runxfail`): `1 failed` (`assert 0 >= 1`). After: `1 passed`
2. `.venv\Scripts\python -m pytest tests/unit/test_structural_chunker.py`
   After: all tests pass, so documents with headings still work

**Risks/Unknowns:**
- No test covers a long document with no headings.
- I'm on Python 3.14.2 and the repo lists 3.11.


---

## Your branch

**Branch**

<!-- [The name of the branch you built the change on, exactly as it appears in your fork. The
naming shape is a type prefix, then the issue number, then a short description. **The issue
number in the branch name must be the number of the issue you claimed** — a name carrying
any other number does not satisfy this field.] -->
fix/56-structural-chunker-no-headings


**Evidence**

<!-- [Your Unit 2 reproduction steps re-run against the built change: the before, then the
after. Paste both, including the commands you ran and their output.] -->
Before (from unit 2 repro — paste your actual output here):
```
>       assert len(result) >= 1
E       assert 0 >= 1
E        +  where 0 = len([])
FAILED tests/unit/test_structural_chunker.py::TestStructuralChunker::test_document_with_no_headings
1 failed in 0.67s

(whole file) 14 passed, 1 xfailed in 0.40s

```

After:
```
tests\unit\test_structural_chunker.py .                                  [100%]
1 passed in 0.28s

(whole file) tests\unit\test_structural_chunker.py ...............  15 passed in 0.31s
```


## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

<!-- [The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.] -->

First/only run: 18/20

**Package analysis**

<!-- [Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.] -->
- Score package: pkg-14
- Rubrid decided: reject (failed:scope)
- Gold label: accept
- Explanation:
 The plan named the files it would touch and described one bounded change, but my scope check requires specific file names and what will change in each. The plan had the file names but the description of the change was brief enough that the skill judged it too vague. Gold accepted it because the change was clearly bounded even if not spelled out in detail

**Check rationale**
<!-- 
[Quote one check from the `rubric.md` you uploaded to `tools/plan-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.] -->

"| scope | The list of files and changes stated anywhere in the plan | The plan names the specific files it will touch and what it will change in each; vague references without file names fail; changes outside the bug's scope fail | required |"

I wrote it to require file names because the group activity showed that without them, Claude looked for a "scope section" heading and hallucinated one when it wasn't there. Anchoring the check to actual file names makes it concrete and harder to fake.

**Trade-offs**

<!-- [Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.] -->

The scope check rejected pkg-14, which gold accepted. The check is strict enough to catch scope creep but it also rejects plans where the files are named but the description of the change is brief. A plan that says "fix chunk() in structural_chunker.py" is probably fine in practice, but my check asks for what will change in each file, not just which file.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
