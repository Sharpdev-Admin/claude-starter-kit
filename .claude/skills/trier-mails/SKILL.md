---
name: trier-mails
description: >
  Use this skill when the owner asks to sort, classify or review incoming e-mail: "trie mes
  mails", "classe ma boîte", "qu'est-ce qui est arrivé", "range mes mails par activité", "fais
  le tri", "qu'est-ce que j'ai en attente". Works either through a connected mailbox (Gmail,
  Outlook, or whatever connector is available) or on e-mails exported into `_inbox/`. Categorises
  each message by activity and request type, applies the filing rules in `contexte/activites.md`,
  creates a fiche for anything that needs follow-up, and — only at trust level 2 or above —
  prepares reply drafts through the `email-reply-drafter` agent. Never sends, never deletes.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /trier-mails — classify, file, flag, and (when allowed) draft

Read `contexte/activites.md` (activities, categories, filing rules), `contexte/style-de-reponse.md`
and `contexte/niveau-de-confiance.md` first. The trust level decides Step 5.

## Step 1 — Establish the source and the window

- If a mailbox connector is available in this session, use it: fetch unread or unlabelled
  messages since the last run (the last run's date is the latest file under
  `tasks/session_reviews/` mentioning `/trier-mails`, else the last 7 days).
- Otherwise use the e-mails exported into `_inbox/`.
- Say which source and which window you are using before going further.

## Step 2 — Qualify each message with a cheap agent

Spawn `email-qualifier` per message (batches of up to 8). Each returns: activity, category,
sender dossier slug if known, one-line gist, whether a reply is expected, urgency, and whether a
fiche is needed (anything with a request, a deadline, an amount or a document gets a fiche;
newsletters and notifications do not).

## Step 3 — Apply the filing rules

- Rules listed in `contexte/activites.md` ("tout ce qui vient de X va dans le dossier Y") are
  applied as labels / folders in the mailbox when a connector allows it, else recorded in the
  report. A message already carrying a "trié" label (or the label set in `contexte/`) is skipped.
- Mark every message you processed with the "trié" label so the owner can see in the mailbox
  what is done and what is not. If the connector cannot label, say so and propose an alternative.
- Never delete. A category the owner wants deleted is moved to a folder named for it instead,
  until the owner writes level 4 for that category.

## Step 4 — Fiches and dossiers

For every message that needs a fiche, run the fiche step of `/ingest-inbox` (Steps 2 to 4 of
that skill) so the message and its attachments exist as markdown in `ressources/` and are linked
to the sender's dossier.

## Step 5 — Replies, strictly by trust level

| Level | What you do with messages that expect a reply |
|---|---|
| 1 | list them in the report with the gist and a one-line suggestion of what the reply should say; write nothing |
| 2 | spawn `email-reply-drafter` per message; save drafts as `ressources/<date>_<slug>/brouillon.md` or as mailbox drafts **without recipient** |
| 3 | same, as mailbox drafts **with recipient pre-filled**; the owner clicks send |
| 4 | send only for the categories listed at level 4 in `contexte/niveau-de-confiance.md`; everything else as level 3 |

If the trust file is missing or unclear, act as level 1 and say so.

## Step 6 — Report

One table sorted by urgency: sender, activity, category, gist, action taken, next step for the
owner (reply / validate draft / nothing). Then the counts: processed, filed, fiches created,
drafts prepared, skipped (already sorted). Commit the repository changes.

## Learning loop (observation phase)

When the owner asks "regarde comment j'ai répondu" or every ~10 processed messages during level
1 and 2: compare the owner's sent replies (connector `sent` folder, or copies dropped in
`_inbox/`) with the gists you produced, extract patterns, and append dated rows to
`contexte/style-de-reponse.md` "Patterns observés". Propose each pattern before writing it.
