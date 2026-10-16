# Guide de démarrage — incrémental, un business à la fois

> Le conseil de base de la discussion : **ne pas chercher la solution finale**. Choisis l'activité
> qui te prend le plus de temps en tâches répétitives et chiantes, mets le système en place pour
> celle-là, et étends ensuite. Nathan est reparti de zéro plusieurs fois avant d'arriver à quelque
> chose de stable, c'est normal.

## Vue d'ensemble

| Étape | Durée indicative | Ce que fait Claude | Ce que tu fais | Niveau de confiance |
|---|---|---|---|---|
| 0. Installation | 1 soirée | Lit le repo, t'interroge, remplit `contexte/` | Réponds à ses questions, connecte ta messagerie | — |
| 1. Observation et tri | ~2 semaines | Trie les mails entrants, crée les fiches `ressources/` | Tu réponds toi-même, comme d'habitude | 1 — trier |
| 2. Brouillons | ~1 à 2 semaines | Rédige des brouillons de réponse (jamais d'envoi) | Tu relis, corriges, envoies. Post-mortem sur les écarts | 2 puis 3 — brouillons |
| 3. Recettes et agents | en continu | Extrait les recettes qui marchent (Pareto), crée agents et skills | Tu valides, tu recadres | 3 |
| 4. Extension | quand c'est stable | Étend aux autres activités, routines de nuit, panels de relecture | Tu arbitres ce qui est commun / spécifique | 3 à 4 par catégorie |

Le niveau de confiance courant est noté dans `contexte/niveau-de-confiance.md`. Claude ne monte
jamais d'un niveau tout seul : c'est toi qui l'écris.

---

## Étape 0 — Installation (une soirée)

1. Fais les 5 points du `README.md` (compte GitHub, repo, connexion Claude ↔ GitHub, première
   session avec `PROMPT-INSTALLATION.md`).
2. **Connecteurs.** Dans Claude, menu *Connecteurs* (ou *Paramètres > Connecteurs*) :
   - **Messagerie.** Pendant la discussion, Nathan n'a pas trouvé de connecteur officiel pour
     Spark. À vérifier dans la liste du jour. Si Spark n'y est pas, deux solutions :
     - connecter directement les comptes sous-jacents (Gmail / Google Workspace, Outlook) — c'est
       ce qui donne le plus de valeur, Claude lit et crée des brouillons directement dans la boîte ;
     - ou, pour commencer sans rien connecter, exporter les mails à traiter dans `_inbox/`
       (un `.eml` par mail, ou un copier-coller du texte dans un `.md`).
   - **Agenda** (Google Calendar, Outlook) : utile dès l'étape 2 pour les prises de rendez-vous.
   - **Google Drive** : un connecteur par compte Google ; vérifie si tu peux en brancher plusieurs
     (deux drives = deux comptes). Sinon, un seul au début, l'autre plus tard.
   - **Notion** : optionnel. Garde-le pour l'organisation transversale (to-do du matin, revues
     quotidiennes), pas pour la base de connaissances : celle-ci vit dans le repo.
3. **Première session.** Colle `PROMPT-INSTALLATION.md`. Claude va :
   - te demander quelles sont tes activités, tes adresses mail, les catégories de demandes que tu
     reçois, comment tu veux qu'on te parle ;
   - remplir `contexte/activites.md`, `contexte/style-de-reponse.md`,
     `contexte/niveau-de-confiance.md` ;
   - te proposer la première action concrète (généralement : trier ce qu'il y a dans ta boîte ou
     dans `_inbox/`).
4. Termine la session par `EOS`. Ça déclenche la revue de fin de session (`.claude/skills/eos/`).

**Important :** parle-lui simplement, en français, comme à un stagiaire. Ne lui explique pas
*comment* faire, dis-lui *quoi* obtenir et pose des limites. Les modèles actuels se débrouillent
mieux sans micro-management ; si tu lui dis comment, c'est toi qui mets le bâton dans l'engrenage.

---

## Étape 1 — Observation et tri (~2 semaines)

Objectif : Claude apprend tes demandes et ta façon d'y répondre, sans rien envoyer.

- Demande-lui : *« Trie mes mails entrants en catégorisant leur contenu par rapport à mes
  activités (voir `contexte/activites.md`). Si tu trouves d'autres catégories, crée-les. Je dois
  pouvoir voir dans ma boîte ce qui est déjà trié et ce qui ne l'est pas. »*
  C'est le skill `/trier-mails`.
- Pour tout ce qui arrive (mail, pièce jointe, PDF), Claude crée **une fiche courte en markdown**
  dans `ressources/` **avant tout traitement**. Lecture avec un petit modèle (Haiku). C'est le
  skill `/ingest-inbox`. Au bout de quelques semaines, il n'aura qu'à relire 200 caractères par
  fiche pour retrier ou réorganiser, au lieu de relire tous les fichiers.
- Toi, tu réponds comme d'habitude. Régulièrement : *« Regarde toutes les réponses que j'ai
  envoyées par rapport à ce que tu avais trié. Tu es mon stagiaire : identifie des patterns dans
  mes réponses et une bonne manière de procéder. Sauvegarde ce que tu trouves dans
  `contexte/style-de-reponse.md`. »*
- Les règles de tri simples (*« tout ce qui vient de telle adresse va dans tel dossier et est
  désépinglé »*) : dis-les une fois, demande-lui de les enregistrer comme règle. Même mal formulé,
  c'est sauvé.

---

## Étape 2 — Brouillons (~1 à 2 semaines)

Objectif : Claude rédige, tu décides.

- *« Maintenant je te laisse un peu plus d'autonomie : tu rédiges les réponses, mais en brouillon
  dans ma boîte, destinataire pré-rempli. Tu n'envoies jamais. »* Passe
  `contexte/niveau-de-confiance.md` à 2 (brouillon sans destinataire) puis 3 (brouillon avec
  destinataire, tu cliques *Envoyer*).
- Pourquoi des brouillons dans la boîte mail plutôt que dans le chat : copier-coller depuis le
  PC ou le téléphone est beaucoup plus simple, et tu gardes le brouillon original à côté de ta
  réponse réelle.
- **Post-mortem.** Quand tu as dû modifier un brouillon, ne passe pas à la suite. Dis :
  *« Compare ton brouillon et ce que j'ai réellement envoyé. Pourquoi j'ai dû modifier ? »* Il va
  soit comprendre tout seul, soit te poser la question. Dans les deux cas, la leçon va dans
  `tasks/lessons.md` (via `EOS`). Tu n'es même pas obligé de lui dire qu'il avait tort : il le
  voit à ce que tu as envoyé.
- Si le même cas revient trois fois et que tu as trois fois des choses à refaire, c'est qu'il n'a
  pas appliqué la recette (ou l'a refaite from scratch). Dis-le-lui : *« tu as utilisé la mauvaise
  recette »*, il ira en chercher une autre.

---

## Étape 3 — Recettes et agents (en continu)

Objectif : transformer ce qui marche en procédures et en employés spécialisés.

- *« Trouve-moi les recettes qui fonctionnent la plupart du temps, loi de Pareto : les 20 % de
  recettes qui couvrent 80 % des cas. Extrais-les et réutilise-les. »* Chaque recette validée
  devient un skill (`/sauvegarder-recette`).
- Les agents : **ne les écris pas toi-même.** Dis : *« Crée-moi un prompt pour telle tâche. »*
  Teste. Quand ça marche : *« Crée un agent pour ce prompt, pour le réutiliser dans le futur. »*
  Claude écrit le fichier dans `.claude/agents/`. Ce qui compte dans un agent, ce n'est pas le nom,
  c'est la **description** : c'est elle qui fait que Claude choisit cet agent plutôt qu'un
  généraliste. Si tu vois que ton agent n'est jamais utilisé, demande : *« Pourquoi tu n'as pas
  utilisé mon agent qui traite les mails ? »* Il va corriger la description.
- Modèles : un modèle léger (Haiku) suffit pour lire, extraire, chercher. Garde les gros modèles
  pour réfléchir et rédiger. Dis-lui : *« tu choisis toi-même le modèle par tâche, mais ne flingue
  pas ma session de la semaine »*.
- Pas d'agent coordinateur : c'est Claude dans ta session qui lit le mail avec un sous-agent qui le
  qualifie, puis délègue au bon agent. Quatre petits agents vont beaucoup plus vite qu'un gros qui
  fait tout de A à Z et sature sa mémoire.

---

## Étape 4 — Extension

- **Plusieurs activités, plusieurs repos.** La structure conseillée à terme : un repo **global**
  (ce qui est commun : ta façon de répondre, tes recettes génériques, l'agent qui parle comme toi),
  plus **un repo par activité** (contexte, secrets, agents propres à cette activité — par exemple
  des réponses en anglais pour l'une et en français pour l'autre). Dans une session Code tu inclus
  un ou plusieurs repos selon le travail à faire. Quand tu vois des recouvrements entre repos :
  *« Fais du clean-up, trouve ce qui est commun et propose-moi de le remonter dans le global. »*
  Laisse-le chercher et proposer ; si tu interviens trop tôt, tu mets ta logique d'humain à la
  place de la sienne.
- **Un dossier = une branche** (optionnel, quand tu es à l'aise). Pour un cas particulier (un
  patient, un client), Claude travaille dans une branche du repo ; quand le cas est clos, tu
  rapatries dans la branche principale uniquement les améliorations générales (le *merge*), le
  contenu du cas reste dans sa branche. Le suivi reste trouvable, le global reste propre.
- **Routines de nuit** (*Scheduled tasks* dans Claude). Exemple : chaque soir, *« liste toutes mes
  tâches en attente, les échéances, les suivis à faire, et prépare-moi le point du matin »*. Tu te
  vides la tête pour la nuit et le produit est prêt le lendemain. Plus touchy à mettre en place ;
  à voir avec Nathan quand le reste tourne.
- **Production de contenu avec panel de relecture.** Pour un contenu important (formation, page de
  vente, CGV) : *« Instancie des agents relecteurs : formateur, client, expert marketing, juriste,
  photographe… au moins 7 profils. Tant qu'ils ne sont pas satisfaits à 95 % chacun, tu continues.
  Pour le juridique, 98 %. »* C'est le skill `/panel-relecture`. Donne le contexte général de
  chaque profil, pas le prompt exact : c'est Claude qui écrit les prompts des relecteurs.

---

## Les pièges vus pendant la discussion

- **Perdre un prompt qui a marché.** Tout ce que tu as mis du temps à expliquer se sauvegarde.
- **Commencer par l'agent chef d'orchestre.** Non : d'abord des agents spécialisés.
- **Expliquer le comment.** Donne le quoi, le contexte et les limites.
- **Laisser Claude prendre des raccourcis.** Garde la recette complète ; s'il la zappe trois fois et
  plante la quatrième, tu repars de zéro. *« Tu fais toutes les étapes de la recette, même si tu
  perds du temps. »*
- **Faire relire le même PDF quinze fois.** D'où les fiches markdown dans `ressources/`.
- **Dupliquer l'information.** La fiche d'un patient référence ses ressources, elle ne les copie
  pas. Pour chercher « tous mes patients qui ont tel problème », Claude parcourt `ressources/`, pas
  chaque dossier.
- **Les connecteurs consomment du contexte.** Ce n'est plus vraiment un problème aujourd'hui pour
  une session de revue du matin où tu actives tout ; pour une tâche précise, dis-lui où est
  l'information plutôt que de le laisser chercher partout.
