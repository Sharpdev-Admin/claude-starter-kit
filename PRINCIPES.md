# Principes — ce qu'on a dit le 16 octobre, en douze règles

Chaque règle renvoie au moment du transcript
(`ressources/2026-10-16_discussion-nathan-nicolas/transcript.md`) où elle a été dite, pour
retrouver le contexte exact. Ces règles sont aussi encodées, en anglais, dans `CLAUDE.md`, le
fichier que Claude lit à chaque session.

## 1. Rien ne se perd : tout le travail de prompt se sauvegarde `[06:42]`

*« Tout le travail que tu te mets à perdre avec lui, à prompter, il faut tout sauvegarder. Et donc
l'idéal c'est d'avoir un système de dossier. »* Chaque recadrage, chaque longue discussion qui
aboutit, chaque recette : dans le repo. Même mal fait, au moins c'est sauvé `[47:46]`.

## 2. Le repo principal est un bac à sable `[31:57]`

On commence avec un seul repo, celui-ci. Il peut être jeté. Les repos par activité et le repo
global viennent plus tard, quand on sait ce qui est commun `[16:17]` `[15:02]`.

## 3. Un dossier de dépôt brut, au nom « bien merdique » `[17:36]`

*« C'est là que tu dois mettre tous mes e-mails bruts, tous mes documents, vraiment le contenu
brut, et tu t'occupes toi de gérer tout ce que tu veux au niveau de la structure sous-jacente. »*
C'est `_inbox/`. Toi tu déposes, Claude range. *« Pour les outputs, tu te débrouilles mais je veux
que les résultats soient parfaits. »*

## 4. Tout devient markdown avant traitement, lu avec un petit modèle `[34:35]` `[34:59]` `[36:13]`

Un mail ne reste pas en `.eml` ou `.msg` : le contenu, les pièces jointes, tout passe dans un
fichier markdown. Un PDF devient un résumé markdown avec le contexte (quel client, quelle date…).
Lecture avec Haiku : il a tout ce qu'il faut, pas besoin d'un gros modèle. Sur le long terme, ça
économise du temps de traitement et évite que la mémoire de Claude grossisse juste pour relire des
PDF déjà lus quinze fois.

## 5. Ressources d'un côté, dossiers de l'autre, sans duplication `[37:18]`

La fiche d'une personne (`dossiers/`) **référence** ses ressources (`ressources/`), elle ne les
copie pas. Pour un screening sur tous tes patients, Claude lit les fiches ressources, pas chaque
dossier. Si une ressource n'est pas référencée dans la fiche de la personne, Claude l'enrichit ou
fait pointer la ressource. Ça vaut pour un patient, un client, un fournisseur.

## 6. Le statut d'urgence vit dans la fiche, l'historique dans les archives `[39:40]`

La fiche d'un fournisseur ne contient pas le PDF de la facture (tu en as besoin une fois par an),
juste le numéro et le lien. Ce qui est en cours est dans la fiche ; une fois la tâche terminée, elle
est flushée vers un historique des interactions. Sois le plus granulaire possible, mais c'est
Claude qui ordonne la structure.

## 7. Apprentissage par essai, erreur, réponse `[03:47]` `[32:44]`

Phase 1 : Claude trie, tu réponds, il observe (deux semaines). Phase 2 : il répond en brouillon,
tu valides, quitte à copier-coller. Tu gardes son brouillon à côté de ta vraie réponse ; il voit
la différence tout seul. Phase 3 : destinataire pré-rempli, tu fais *send, send, send*. Phase 4 :
pour les demandes récurrentes, il envoie. *« Là tu passes dans un nouveau spoiler : tu fais
confiance à tes agents. Ils ont été entraînés sur tes cas bien spécifiques. »*

## 8. Toujours un post-mortem, et la revue de fin de session `[22:18]` `[22:33]`

Quand un résultat te satisfait, ce n'est pas *« ok c'est bon, je passe à la suite »*. Tu prends
le temps de la revue : ce que Claude a généré et que tu as dû modifier, et pourquoi. Le skill de
fin de session (`EOS`) relit les prompts des agents, leurs résultats, l'efficacité, la dérive de
scope. S'il a dû poser trop de questions, c'est que le job n'était pas clairement identifié au
départ. Les leçons vont dans la mémoire générale (`tasks/lessons.md`).

## 9. Des agents spécialisés, pas un chef d'orchestre `[41:24]`

Un agent qui coordonne tout va vouloir tout faire lui-même et ne déléguera pas ; sa session gonfle,
se compresse, et il ne comprend plus. Des agents qui ont chacun une tâche spécifique vont super
vite et font bien leur job, comme des employés dédiés. C'est Claude, dans ta session, qui lit le
mail via un sous-agent qualifieur et délègue au bon agent.

## 10. Tu ne crées pas les agents, tu les fais créer `[41:05]` `[42:50]`

*« Crée-moi un prompt pour telle tâche. »* Tu testes. *« Maintenant crée un agent pour ce prompt
dans le but de le réutiliser dans le futur. »* Un agent, c'est un nom, une description, un modèle,
un nombre de tours maximum, et la description du job. **La description est ce qui compte** : si
Claude ne prend jamais ton agent, c'est qu'elle est mal écrite (par exemple en anglais alors que tu
demandes toujours en français) `[44:47]`. Dis-le-lui, il la corrige.

## 11. Dis le quoi, pas le comment ; choisis le modèle par tâche `[21:11]`

Donne le contexte et les limites, pas la méthode. Pour des recherches ou de la lecture, un petit
modèle suffit. *« Tu détermines toi-même le modèle, mais essaie de ne pas flinguer ma session de la
semaine. »* Les recettes complètes restent obligatoires : s'il prend des raccourcis trois fois, la
quatrième plante.

## 12. Panel de relecture à 95 % pour le contenu `[18:26]` `[18:49]`

Pour un contenu à produire : instancier des sous-agents bêta-testeurs (formateur, client, expert
marketing, juriste, photographe… au moins sept) et continuer tant qu'ils ne sont pas satisfaits à
95 % chacun, 98 % pour du juridique. Pas trop restrictif, sinon ça tourne sans fin. Tu donnes le
contexte général de chaque profil ; Claude écrit lui-même les prompts.

---

## Et aussi, en vrac

- **Brouillons dans la boîte mail** plutôt que dans le chat ou WhatsApp : plus simple à copier
  depuis le PC et le téléphone `[03:47]`.
- **Notion** : utile pour l'organisation transversale (revues du matin, to-do), pas pour la base
  de connaissances, qui vit dans GitHub `[23:48]` `[27:16]`.
- **GitHub est fait pour ça** : une branche par cas particulier, un merge vers la branche
  principale uniquement pour les améliorations générales `[24:12]`.
- **Routines** (*Scheduled tasks*) : des travaux de nuit qui préparent le point du matin
  `[29:45]`. Plus tard.
- **Connecteurs** : ils consomment du contexte, mais aujourd'hui ce n'est plus vraiment un
  problème pour une session de revue où tu actives tout `[23:48]`.
