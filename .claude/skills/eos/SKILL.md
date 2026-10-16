---
name: eos
description: >
  Run this skill when the owner ends a working session: "EOS", "fin de session", "on arrête
  là", "post-mortem", "fais le bilan", "qu'est-ce que tu as appris aujourd'hui", "sauvegarde et
  termine". Reviews the session for corrections and recipes, proposes lessons one by one for
  approval, saves only what is approved, writes the session review, commits and pushes the
  repository. Nothing is saved without an explicit yes.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, AskUserQuestion]
---

# /eos — end of session: learn, save, commit

## Step 1 — Analyse the session (silently)

Go through this session's conversation and tool calls and collect:

- **Corrections**: every message where the owner corrected, redirected, re-explained or said
  "non". Keep their exact words.
- **Questions you had to ask**: if there were many, the job was not clear at the start — a
  lesson about how the owner should brief you, or about what `contexte/` lacks.
- **Results the owner called good**: candidates for `/sauvegarder-recette` if not saved yet.
- **Agents used**: which agent did what, whether it was picked when it should have been, and
  whether its output had to be redone by hand. An agent that was not picked for a job it exists
  for means its description must change.
- **Drafts the owner modified before sending** (level 2 and up): the diff and the reason.
- **Facts learned about the owner or an activity** not yet in `contexte/`.

Check `tasks/lessons.md` so you do not propose a lesson that already exists.

## Step 2 — Propose, one item at a time

Present the candidates as a numbered list, each in two lines (the rule, and why), with where it
would be saved: `tasks/lessons.md`, a `contexte/` file, a skill or agent file. Then ask the owner
to approve, reject or reword each one — use `AskUserQuestion` with at most 4 items per question.
If there is nothing new, say so and go to Step 4.

If the owner answers "plus tard": save the draft as
`tasks/session_reviews/<YYYY-MM-DD>_<HH-MM>_pending.md` and stop after Step 5.

## Step 3 — Save only what was approved

- Rules: prepend to `tasks/lessons.md` in the file's format, numbered after the last `L<n>`.
- Facts: edit the right `contexte/` file.
- Agent description fixes: edit the agent file; say what changed.
- Recipes: run `/sauvegarder-recette` for each.

Never save a rejected or unanswered item.

## Step 4 — Write the session review

`tasks/session_reviews/<YYYY-MM-DD>_<HH-MM>_reviewed.md`: date, what was done (5 lines
maximum), corrections received (verbatim), lessons saved / rejected, open items for next time,
and the first thing to do next session in one line. Delete a `_pending.md` of the same session
if it existed.

## Step 5 — Commit and push

```
git add -A
git commit -m "EOS <YYYY-MM-DD>: <one line on what the session did>"
git push
```

Check `git status` is clean afterwards and that the push succeeded; if it did not, say so and
give the exact error. Before committing, confirm `secrets/` is still ignored
(`git check-ignore -q secrets/README.md` must exit 1, i.e. tracked; for any other file under
`secrets/`, `git check-ignore -q <file>` must exit 0, i.e. ignored).

## Step 6 — Close

Three lines to the owner: what was saved, the review path, the first action for next time.
