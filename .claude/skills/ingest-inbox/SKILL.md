---
name: ingest-inbox
description: >
  Use this skill when the owner asks to process what they dropped in the raw inbox folder:
  "traite l'inbox", "range ce que j'ai déposé", "fais les fiches", "traite les nouveaux
  documents", "process _inbox", or when a session starts and `_inbox/` is not empty. Converts every
  raw item (e-mail export, PDF, image, pasted text, transcript) into a short markdown fiche in
  `ressources/`, links it to the right `dossiers/` entry, and moves the original next to its
  fiche. Reading is delegated to cheap-model agents; the main session only orchestrates and
  verifies.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /ingest-inbox — raw items become fiches before anything else

Read `CLAUDE.md` §2 and §3 first: markdown first, resources separate from dossiers, no
duplication. Read `contexte/activites.md` to know the activities and their categories.

## Step 1 — Inventory

1. List everything under `_inbox/` except `README.md`. Group an e-mail and its attachments
   together (same base name, or a sub-folder with the same name).
2. Print the inventory to the owner in one short table: item, type, size. If there are more than
   30 items, ask whether to process all of them now or only the most recent N.
3. If an item is unreadable (encrypted PDF, image with no text, corrupted file), say so in the
   final report; do not guess its content.

## Step 2 — One fiche per item, by a cheap agent

For each item (or e-mail group), spawn one agent **in parallel batches of up to 8**:

- `email-qualifier` for an e-mail (with its attachments listed);
- `document-summarizer` for any other document.

Brief each agent with: the absolute path of the item, the path of
`ressources/_template-fiche-ressource.md`, the activity list from `contexte/activites.md`, and
the output path `ressources/<YYYY-MM-DD>_<slug>/fiche.md` where the date is the source's date
and the slug is short, lowercase, hyphenated, in French. The agent writes the fiche itself.

## Step 3 — Verify the boundaries, not a sample

Before linking anything, print the first and last line of **every** fiche produced and read
them. A fiche that starts or ends in the wrong place (a signature, a quoted reply, an empty
summary) is redone, not patched. Check that every fiche has the frontmatter fields filled; an
empty `activite` or `date` is a defect.

## Step 4 — Link to dossiers

For each fiche, for each person or entity it names:

1. Look for an existing dossier (`Grep` the slug or name under `dossiers/`).
2. If found: add a row to its "En cours" or "Historique" table pointing at the fiche, and add the
   dossier slug to the fiche's `personnes` list.
3. If not found: create the dossier from `dossiers/_template-fiche-dossier.md` with what the
   fiche establishes, nothing invented. Mark unknown fields `<à compléter>`.

Never copy a fiche's content into a dossier; link it.

## Step 5 — Move originals

Move each original from `_inbox/` into its fiche's folder, unless `contexte/` or the owner said
originals of that type are not kept (then delete only after the fiche is verified, and say so).
`_inbox/` must be empty of processed items at the end; items that failed stay there and are
listed in the report.

## Step 6 — Report and commit

Print one table: fiche path, type, activity, dossiers linked, status. State how many items were
processed, how many failed and why. Then `git add` the new and changed files and commit with a
message like `Ingest: N items (YYYY-MM-DD)`. Do not push unless the session is ending.

## What this skill never does

- It never replies to anything, never sends, never deletes an e-mail in a mailbox.
- It never reads an original in the main session when an agent can do it.
- It never invents a date, an amount or a name that is not in the source: unknown stays
  `<inconnu>` in the fiche.
