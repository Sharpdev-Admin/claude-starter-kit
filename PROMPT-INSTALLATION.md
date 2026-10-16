# Prompt d'installation — à coller tel quel dans ta première session Claude Code sur ce repo

Copie tout ce qui est entre les lignes `---` et colle-le comme premier message. Claude fait le
reste et te pose les questions nécessaires.

---

Tu travailles sur mon repo `claude-starter-kit`. C'est ma base pour te déléguer mon quotidien
(mails, demandes, rendez-vous, documents, production de contenu). Le repo a été préparé pour moi
par un ami ; je débute avec Claude Code et je ne suis pas développeur.

Commence par lire, dans cet ordre : `README.md`, `PRINCIPES.md`, `GUIDE-DEMARRAGE.md`, puis
`CLAUDE.md` (tes instructions) et la fiche
`ressources/2026-10-16_discussion-nathan-nicolas/fiche.md` qui résume la discussion d'origine.
Lis les fichiers en entier.

Ensuite, fais exactement ceci :

1. **Interroge-moi** pour remplir `contexte/` — par lots de 4 questions maximum, avec des
   propositions de réponse quand c'est possible. Je dois pouvoir répondre vite. Ce que tu dois
   établir :
   - mes activités (le fichier `contexte/activites.md` contient des noms relevés dans le
     transcript, probablement mal orthographiés : fais-les-moi confirmer un par un) ;
   - mes adresses mail, par activité, et l'outil que j'utilise pour les lire ;
   - les connecteurs que j'ai réussi à activer dans Claude (messagerie, agenda, drive, Notion) ;
   - les catégories de demandes que je reçois le plus souvent, et celle qui me prend le plus de
     temps en tâches répétitives : c'est par là qu'on commence ;
   - la langue et le ton de mes réponses, par activité ;
   - le niveau d'autonomie que je t'accorde aujourd'hui (voir `contexte/niveau-de-confiance.md` ;
     on démarre au niveau 1 : tu tries, tu n'envoies rien).
2. **Écris les réponses** dans `contexte/activites.md`, `contexte/style-de-reponse.md` et
   `contexte/niveau-de-confiance.md`. Pas de mot de passe ni de clé dans ces fichiers ni dans le
   chat : si tu as besoin d'un accès, dis-moi quel fichier créer dans `secrets/` et je l'écris
   moi-même.
3. **Propose-moi la première action concrète** pour l'étape 1 du guide (observation et tri),
   adaptée à ce que j'ai répondu : soit trier ma boîte via le connecteur, soit traiter ce que je
   dépose dans `_inbox/`. Une seule action, pas un plan sur six mois. Attends mon accord avant de
   la lancer.
4. **Adapte le kit à moi** si quelque chose dans les skills ou agents ne colle pas à mes réponses
   (par exemple la langue des réponses, les catégories de tri). Dis-moi ce que tu as changé.
5. **Termine la session par la revue de fin de session** (`/eos`) : ce que tu as appris de moi
   aujourd'hui va dans `tasks/lessons.md`, et tu commits tout dans le repo.

Règles pour toute la suite de notre collaboration : tu me parles en français, simplement, sans
jargon technique sauf si je le demande ; quand je te recadre, tu sauvegardes la leçon ; quand une
recette marche, tu me proposes de la sauvegarder ; tu n'envoies jamais un mail et ne supprimes
jamais rien sans que je l'aie demandé explicitement.

---
