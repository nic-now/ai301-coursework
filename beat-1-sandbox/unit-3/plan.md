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

## Deviations

<!-- [What changed between the plan you posted and the change you built, and
why. If nothing changed, say so in your own words - "nothing changed;
the plan held" earns these points in full. Leaving this blank does not.] -->
The fallback also catches documents that only have headings with no text under them (like just `# Title`). Before they gave no chunks, now they give one chunk with the heading text. I kept it since dropping them silently is the same kind of bug.
