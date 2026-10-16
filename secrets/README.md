# secrets/ — identifiants et clés d'accès

Ce dossier est **ignoré par git** (voir `.gitignore` à la racine) : rien de ce que tu mets ici ne
part sur GitHub. C'est le seul endroit du repo où un mot de passe, une clé API ou un jeton a le
droit d'exister.

## Règles

- **Jamais dans le chat.** Si Claude a besoin d'un accès, il te dit quel fichier créer ici et tu
  l'écris toi-même. Il ne te demande jamais de coller un mot de passe dans la conversation.
- **Un fichier par service**, nommé clairement : `secrets/google-drive-tembo.md`,
  `secrets/site-kine.md`. Le contenu est libre (identifiant, mot de passe, URL, notes).
- Claude peut **lire** ces fichiers pour vérifier qu'un accès existe ; il ne recopie jamais la
  valeur ailleurs (ni dans une fiche, ni dans une leçon, ni dans un commit).
- La plupart des accès (messagerie, agenda, drive, Notion) passent par les **connecteurs** de
  Claude et n'ont pas besoin d'être écrits ici.

## Attention

Si un jour tu changes le `.gitignore` ou que tu copies ce repo ailleurs, vérifie que `secrets/`
reste ignoré : `git check-ignore -v secrets/mon-fichier.md` doit répondre avec la ligne du
`.gitignore`. Demande à Claude de le vérifier, il sait faire.
