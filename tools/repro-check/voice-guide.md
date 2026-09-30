# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I am a student learning open source contribution as part of a course. I am here to help with a specific issue, not to take over or make big decisions. Maintainers can expect short, clear, and honest comments from me.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

### Rule: say what you found, not what you tried

State the result of your reproduction attempt, not the effort you put in.

- Wrong: "I spent a while trying to reproduce this and followed all the steps."
- Right: "I was able to reproduce this on Python 3.11 and macOS 14."

### Rule: no promises you cannot keep

Do not say you will fix or submit a PR unless you are sure you can and will.

- Wrong: "I'll have a fix ready soon!"
- Right: "I reproduced the issue and can open a PR if no one else is working on it."

### Rule: be specific about what you saw

Name the exact error, output, or behavior. Vague descriptions waste the maintainer's time.

- Wrong: "It didn't work as expected."
- Right: "Running the command throws a KeyError on line 42 of utils.py."

### Rule: disclose AI use if the repo asks

If the repo has an AI policy or disclosure requirement, mention it. If it does not, skip it.

- Wrong: (posting a comment with no disclosure when CONTRIBUTING.md requires it)
- Right: "Note: I used AI assistance to help reproduce this issue, as required by the contribution policy."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- "I'll fix this" when I have not confirmed I can
- "This is easy / quick fix" as a way to claim the issue without proof
- Vague statements like "it doesn't work" with no specifics
- Over-explaining my process instead of just stating the result
- Anything that sounds like I am correcting or criticizing the maintainer
