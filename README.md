# Claude Starter Kit — ta base pour déléguer ton quotidien à Claude

Ce dossier est le point de départ dont on a parlé le **16 octobre 2026** (le transcript complet de
la discussion est dans `ressources/2026-10-16_discussion-nathan-nicolas/`). Ce n'est pas la
solution finale à tous tes problèmes : c'est le **bac à sable**, le repo principal que tu vas
nourrir petit à petit, et que tu peux jeter et recommencer si tu te rends compte que tu n'es pas
efficace.

## Les trois idées à garder en tête

1. **Rien de ce que tu apprends à Claude ne doit être perdu.** Chaque discussion où tu le recadres,
   chaque recette qui marche, chaque réponse que tu as dû corriger : ça se sauvegarde ici, dans ce
   repo. Sinon tu répètes quinze fois la même chose à un stagiaire qui oublie.
2. **Tout ce qui rentre devient du markdown avant d'être traité.** Un email, un PDF, une facture :
   Claude en fait d'abord une fiche courte en markdown (lue avec un petit modèle, pas cher), et ne
   relit le fichier d'origine que si c'est vraiment nécessaire.
3. **La confiance se gagne par paliers.** D'abord Claude observe et trie. Puis il rédige des
   brouillons que tu envoies toi-même. Puis, pour certaines catégories seulement, il envoie. Jamais
   l'inverse.

## Ce qu'il y a dedans

| Dossier / fichier | À quoi ça sert |
|---|---|
| `GUIDE-DEMARRAGE.md` | **Commence par là.** Le plan semaine par semaine pour mettre ça en place sans te noyer. |
| `PRINCIPES.md` | Les règles de fonctionnement issues de notre discussion, avec le minutage dans le transcript. |
| `PROMPT-INSTALLATION.md` | Le message à coller dans ta première session Claude : il fait le reste. |
| `CLAUDE.md` | Les instructions que Claude lit automatiquement à chaque session sur ce repo. Tu n'as pas besoin de le lire, mais tu peux. |
| `contexte/` | Qui tu es, tes activités, ta façon de répondre, le niveau d'autonomie que tu accordes à Claude. **À remplir avec Claude lors de la première session.** |
| `_inbox/` | La zone de dépôt brute : emails exportés, PDF, notes vocales, n'importe quoi. Tu déposes, Claude range. |
| `ressources/` | Les fiches markdown que Claude produit à partir de `_inbox/`. Une fiche par source. Le transcript de notre discussion y est déjà, comme exemple. |
| `dossiers/` | Une fiche par personne ou entité (patient, client, fournisseur). Chaque fiche **pointe** vers ses ressources, elle ne les copie pas. |
| `.claude/skills/` | Les **recettes** : des procédures réutilisables que Claude applique quand tu le lui demandes (`/trier-mails`, `/eos`, etc.). |
| `.claude/agents/` | Les **agents spécialisés** : des employés avec une seule tâche (qualifier un mail, résumer un document, rédiger un brouillon de réponse). |
| `tasks/lessons.md` | Le carnet de leçons : ce que Claude a appris de tes corrections. Il s'alimente à chaque fin de session (`/eos`). |
| `secrets/` | Là où vont les mots de passe et clés d'accès. **Jamais poussé sur GitHub** (voir `.gitignore`). |

## Démarrer en 15 minutes

1. **Crée un compte GitHub** (gratuit) sur https://github.com si tu n'en as pas.
2. **Mets ce dossier dans un repo à toi.** Deux options :
   - *Si Nathan t'a donné un lien vers un repo GitHub* : ouvre-le, clique **Fork** (ou **Use this
     template** si le bouton existe) pour en faire une copie dans ton compte.
   - *Si tu as reçu un zip* : installe **GitHub Desktop** (https://desktop.github.com), crée un
     nouveau repo privé nommé `claude-starter-kit`, décompresse le zip dans le dossier du repo
     (attention : il contient des fichiers cachés, `.claude/` et `.gitignore`, qu'il faut copier
     aussi — sur Mac, `Cmd+Shift+.` dans le Finder les affiche), puis **Commit** et **Push**.
3. **Connecte Claude à GitHub** : dans Claude, va dans **Code**, nouvelle session, et autorise
   l'accès à ton compte GitHub quand il te le demande (installe l'application Claude sur ton repo).
4. **Ouvre une session Code sur ce repo** et colle comme premier message le contenu de
   `PROMPT-INSTALLATION.md`. Claude va te poser des questions, remplir `contexte/` avec toi, et
   te proposer la première action.
5. **Suis `GUIDE-DEMARRAGE.md`** semaine par semaine. À chaque fin de session, tape `EOS`.

## Ce que ce kit ne fait pas

- Il ne connecte pas tout seul ta boîte mail ni ton agenda : ça se fait dans Claude, menu
  **Connecteurs** (voir le guide, semaine 0).
- Il ne contient aucun agent "chef d'orchestre" qui ferait tout. C'est voulu : un agent qui veut
  tout faire lui-même ne délègue pas, remplit sa mémoire et finit par ne plus comprendre ce qu'on
  lui demande. On construit des petits agents spécialisés, et c'est Claude lui-même qui les appelle.
- Il n'est pas figé. Dès que tu as une recette qui marche, dis à Claude : *« fais en sorte de
  pouvoir réutiliser ça dans le futur, sauvegarde-le dans le repo »*. Même mal fait, c'est sauvé.
