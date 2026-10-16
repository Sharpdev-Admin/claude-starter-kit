# ressources/ — une fiche markdown par source

Chaque chose qui entre (mail, document, facture, transcript, résultat d'examen) a ici **une fiche
courte** qui dit de quoi il s'agit sans qu'on doive rouvrir l'original. C'est ce que Claude lit
quand il doit retrouver une information, retrier, ou faire un screening sur tous tes patients ou
tous tes fournisseurs.

## Convention

- Un dossier `AAAA-MM-JJ_<sujet>/` par source, contenant `fiche.md` (la fiche) et l'original
  s'il est en texte (`.md`, `.txt`, `.csv`). Les originaux lourds (PDF, images) peuvent rester à
  côté ou ailleurs (drive) : la fiche indique où.
- Une fiche seule `AAAA-MM-JJ_<sujet>.md` suffit pour un petit élément (un mail court).
- Le modèle de fiche est `_template-fiche-ressource.md`. Claude le suit ; s'il manque un champ
  utile à ton activité (numéro de patient, numéro de facture, échéance…), demande-lui d'étendre
  le modèle, pas de bricoler fiche par fiche.
- Une fiche ne copie pas le contenu d'une autre. Elle renvoie vers le dossier de la personne
  concernée (`dossiers/...`) et, si besoin, vers d'autres fiches.

## Exemple

`2026-10-16_discussion-nathan-nicolas/` : la discussion qui a donné naissance à ce kit.
`fiche.md` en est le résumé structuré ; `transcript.md` est l'original nettoyé.
