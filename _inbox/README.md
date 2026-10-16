# _inbox/ — la zone de dépôt brut

Tu déposes ici **n'importe quoi, sans ranger** : un mail exporté, un PDF, une facture, une capture
d'écran, un texte collé dans un `.md`, une note vocale transcrite. Claude s'occupe du reste
(`/ingest-inbox`) :

1. il lit chaque élément avec un petit modèle ;
2. il crée une fiche markdown dans `ressources/` (quoi, qui, quand, quelle activité, résumé,
   faits clés, lien vers l'original) ;
3. il rattache la fiche au bon dossier dans `dossiers/` (ou crée le dossier) ;
4. il déplace l'original dans `ressources/<date>_<slug>/` à côté de sa fiche, ou le supprime
   d'ici si tu as dit que l'original ne devait pas être conservé.

Quand `_inbox/` est vide, tout a été traité.

## Conseils

- Un mail : exporte-le (`.eml`) ou colle son texte dans un fichier `.md` avec l'expéditeur, la
  date et l'objet en haut. Les pièces jointes à côté, dans un sous-dossier portant le même nom.
- Pas besoin de nommer proprement : `truc.pdf` convient, Claude renomme.
- Si la messagerie est connectée à Claude, tu n'as plus besoin de passer par ici pour les mails ;
  `_inbox/` reste utile pour les documents qui n'arrivent pas par mail.
