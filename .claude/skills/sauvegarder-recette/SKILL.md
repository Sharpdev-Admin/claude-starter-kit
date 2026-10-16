---
name: sauvegarder-recette
description: >
  Use this skill when the owner is satisfied with a result and wants it reusable: "sauvegarde
  ça", "garde cette recette", "fais en sorte de réutiliser ça dans le futur", "note la
  procédure", "crée un skill pour ça", "crée un agent pour ce prompt". Also use it proactively,
  as a proposal, right after the owner says a result is good. Turns the steps that just worked
  into a skill under `.claude/skills/`, an agent under `.claude/agents/`, or a rule in
  `tasks/lessons.md`, and registers it in `CLAUDE.md` §11.
allowed-tools: [Read, Write, Edit, Glob, Grep, AskUserQuestion]
---

# /sauvegarder-recette — a result that worked becomes reusable

## Step 1 — Decide the shape, with one question at most

Look at what just happened in the session and pick:

| It was | Save it as |
|---|---|
| a sequence of steps the owner will ask for again ("fais X puis Y") | a **skill** |
| one focused job that a worker should do on its own, with its own instructions (qualify, summarise, draft, review) | an **agent** |
| a way of behaving, a thing to always or never do | a **rule** in `tasks/lessons.md` |
| a fact about the owner or an activity | a line in the right `contexte/` file |

If two shapes fit, ask the owner one question with both options described in plain words. Do not
ask about frontmatter fields, tools or models; decide those yourself.

## Step 2 — Write it from what actually worked

- Reconstruct the steps from the session: what was read, in what order, what was produced, what
  the owner corrected. Keep the corrections in; they are the recipe.
- **Skill**: `.claude/skills/<nom-court>/SKILL.md`, frontmatter `name`, `description`,
  `allowed-tools`; body in numbered steps, each with a verifiable outcome; a "never does" list.
  The `description` must contain the French phrases the owner actually uses to ask for it (at
  least 4, quoted), because that is what makes the skill get picked.
- **Agent**: `.claude/agents/<nom-court>.md`, frontmatter `name`, `description`, `model`,
  `tools`, `maxTurns`. Identity in one sentence, inputs it receives, numbered procedure, exact
  output format, guardrails. Model: `haiku` for reading and extraction, `sonnet` for drafting,
  `opus` only if the owner asked for deep judgement. Tools: the minimum; no `Write` for a
  read-only job. The `description` again carries the owner's French trigger phrases.
- **Rule**: the entry format of `tasks/lessons.md`, with the owner's words when they corrected
  you, dated, numbered.

## Step 3 — Register and check

1. Add the skill or agent to the table in `CLAUDE.md` §11 (skills) or the agent list below it.
2. Re-read the new file once as if you were a fresh session that has never seen this
   conversation: is every path absolute or repo-relative, is every step doable without the chat
   context? Fix what is not.
3. Tell the owner, in two lines, what was saved and where, and how to invoke it next time.

## Never

- Never save something the owner did not confirm was satisfactory.
- Never overwrite an existing skill or agent silently: say it exists and propose a merge.
- Never put a secret, an e-mail address list or a patient's data inside a skill or agent file;
  those live in `contexte/`, `secrets/` or `dossiers/` and the skill points at them.
