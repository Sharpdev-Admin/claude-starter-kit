---
name: panel-relecture
description: >
  Use this skill when the owner wants a piece of content reviewed by several points of view until
  it is good enough: "fais relire", "panel de relecteurs", "bêta-testeurs", "fais-le valider par
  un formateur, un client, un juriste", "satisfaction à 95 %", "relecture croisée", "est-ce que
  c'est prêt à publier". Applies to course material, sales pages, e-mail sequences, terms of
  sale, patient leaflets, social posts. Instantiates one `relecteur-critique` agent per reviewer
  profile, scores, revises, and loops until every profile reaches the target score.
allowed-tools: [Read, Write, Edit, Glob, Grep, Agent, AskUserQuestion]
---

# /panel-relecture — a panel of specialised readers, until they are satisfied

## Step 1 — Frame the review (one question round)

Establish, from the owner's request and at most one `AskUserQuestion` round:

- **The content**: path(s) in the repo, or a draft the owner pasted (save it first under
  `ressources/<date>_<slug>/v1.md`).
- **The audience and the goal**: who reads it, what they must do or feel afterwards.
- **The profiles**: at least 7 by default. Propose a panel fitted to the content (for a
  training: trainer, learner, client, marketer, lawyer, designer, sceptic who has seen too many
  trainings; for a patient leaflet: patient, carer, physiotherapist, lawyer, plain-language
  editor, GP, sceptic). The owner adjusts; you write the profiles' context, **not their prompts**.
- **The target**: 95 % per profile by default; 98 % for anything legal or contractual. Keep the
  target realistic: a panel that can never be satisfied runs forever. Maximum rounds: 4, then
  report where it stands.

## Step 2 — Round 1: independent reviews

Spawn one `relecteur-critique` agent per profile, **all in the same batch**, each briefed with:
the content path, the audience and goal, its own profile in two or three sentences (who they
are, what they care about, what makes them reject a piece), the scoring scale (0 to 100), and
the output path `ressources/<date>_<slug>/revue-round1-<profil>.md`. Each agent writes: score,
three strongest objections with the exact passage quoted, what would raise the score to target.

## Step 3 — Consolidate and revise

1. Read every review. Print one table: profile, score, top objection.
2. Group objections. Where two profiles contradict each other (the lawyer wants a caveat the
   marketer wants gone), decide by the goal from Step 1, and write the decision down in
   `revue-decisions.md` with the reason; do not silently pick one side.
3. Produce `v<n+1>.md`. Keep the owner's voice: a revision is the owner's text with the objections
   fixed, not a rewrite in your own style.

## Step 4 — Next rounds

Re-run only the profiles below target, on the new version. Stop when all profiles are at or above
target, or after 4 rounds. Never lower the target to finish; say what is still short.

## Step 5 — Hand back

Give the owner: the final version path, the score table per round, the decisions taken on
contradictions, and the objections left open (with the reviewer's own words). Propose to save
the panel composition as a recipe if the owner will reuse it for this kind of content.

## Never

- Never publish, send or post the content; the owner does.
- Never invent a fact, a testimonial, a legal claim or a figure to satisfy a reviewer: flag it
  as "needs a real source from the owner" instead.
