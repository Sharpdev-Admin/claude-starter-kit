---
type: transcript
date: 2026-10-16
source: appel Nathan Lahy / Nicolas Fassin, transcription automatique (Spinach)
activite: transversal (organisation personnelle)
personnes: []
original: transcript.md
traite_le: 2026-10-16
statut: fait
---

# Discussion du 16 octobre 2026 — comment structurer Claude pour gagner du temps

## En deux lignes

Nicolas n'arrive pas à faire de Claude un gain de temps (mails, demandes, rendez-vous, contenu).
Nathan lui décrit le système qu'il a construit en quelques mois et un plan incrémental pour le
reproduire, en commençant par un seul repo bac à sable.

## Faits clés

- Besoins exprimés par Nicolas (00:05) : gestion des réponses, automatisation des réponses aux
  prises de rendez-vous, gestion des mails et des demandes, production de contenu vérifié. Le
  problème est « un problème de management de mes agents ».
- Activités citées par Nicolas (07:00) : sa pratique de kiné, et deux autres structures dont les
  noms sont rendus approximativement par la transcription (voir *Termes à vérifier*).
- Outils de Nicolas : Spark (messagerie, plusieurs adresses et signatures), Obsidian (ancien
  vault, peu utilisé), deux drives Google (un personnel, un pour une activité), pas encore de
  Notion mais envie de s'en servir pour s'organiser.
- Ce que Nathan a fait chez son client (01:18) : deux mois à nourrir Claude avec des mails de
  support bruts et leurs résolutions ; au bout de trois mois Claude produit directement la
  procédure et le mail à la bonne personne.
- Plan conseillé (16:17, 31:57) : un repo bac à sable d'abord, puis quatre repos (global,
  Nicolas, et un par activité) ; commencer par l'activité la plus chronophage en tâches
  répétitives.
- Première étape concrète convenue (32:06 à 33:30) : brancher la messagerie, faire trier les
  mails entrants par activité avec un marquage trié / non trié, laisser Claude observer les
  réponses pendant environ deux semaines, puis passer aux brouillons.
- Nicolas compte s'y mettre le week-end suivant ; Nathan est en congé la semaine suivante, point
  prévu le lundi en huit (environ 26 octobre 2026).

## Ce qui est demandé / à faire

- Pour Nicolas : créer un compte GitHub, un repo, connecter Claude ; appliquer l'étape 1 du
  `GUIDE-DEMARRAGE.md`.
- Pour Nathan : fournir une structure importable (ce kit) ; reparler des routines (tâches
  planifiées) quand le reste tourne.

## Contenu — les points de la discussion, dans l'ordre

| Minute | Point |
|---|---|
| 00:05 | Besoins de Nicolas : réponses, rendez-vous, mails, demandes, contenu vérifié |
| 01:18 | L'expérience de Nathan : du mail de support brut à la procédure générée |
| 03:47 | Brouillons dans la boîte mail plutôt que dans le chat ; garder le brouillon à côté de la vraie réponse |
| 05:30 | Les paliers de confiance : trier, brouillon, destinataire pré-rempli, envoi |
| 06:42 | Tout sauvegarder ; un système de dossiers ; les recettes complètes sans raccourcis |
| 07:00 | Découpage par activité ; les mêmes demandes peuvent arriver dans les trois |
| 07:47 | Connecteurs : vérifier ce qui existe (Spark non trouvé), Notion pour l'organisation |
| 11:00 | GitHub comme base : un repo global, un par projet ; inclure les repos selon le job |
| 13:30 | Skills (recettes) et agents ; générique versus spécifique à une activité |
| 15:02 | Laisser Claude trouver les recouvrements et proposer, plutôt que d'imposer sa logique d'humain |
| 16:17 | Quatre projets conseillés ; commencer par un seul |
| 16:58 | Extraire les recettes Pareto, les propager aux autres repos |
| 17:36 | Le dossier de dépôt brut : Nicolas alimente, Claude structure |
| 18:26 | Panel de sous-agents bêta-testeurs, satisfaction à 95 % (98 % en juridique) |
| 21:11 | Choisir le modèle par tâche, ne pas flinguer la session de la semaine |
| 22:18 | Post-mortem sur ce qui a été modifié ; le skill de fin de session |
| 23:48 | Où sauvegarder : GitHub, branches par cas, merge des améliorations |
| 27:16 | Notion : utile pour les revues et les to-do, pas pour la base de connaissances |
| 29:45 | Routines de nuit (tâches planifiées) ; à voir plus tard |
| 31:57 | Première étape : bac à sable + messagerie + tri + observation deux semaines |
| 34:35 | Tout en markdown, lecture avec Haiku, résumé par PDF avant traitement |
| 37:18 | Ressources séparées des dossiers ; la fiche référence, ne copie pas |
| 39:40 | Fiche fournisseur : numéro et lien, pas le PDF ; historique des interactions |
| 41:24 | Pas d'agent coordinateur ; des agents spécialisés que Claude appelle |
| 44:47 | La description de l'agent fait tout ; corriger si l'agent n'est jamais pris |
| 47:46 | À chaque résultat satisfaisant : « fais en sorte de le réutiliser, sauvegarde-le » |

## Termes à vérifier avec Nicolas (transcription approximative)

| Dans le transcript | Minute | Lecture probable | Statut |
|---|---|---|---|
| « le Kali Nimbus » | 07:00 | nom de la deuxième activité | à confirmer |
| « Consult&Go » | 07:00 | nom de la troisième activité | à confirmer |
| « Tembo » | 10:20, 16:17 | nom d'une activité ou structure avec son propre drive | à confirmer |
| « Impulse » | 11:00, 14:30 | nom d'une activité (support, documentation PubMed) | à confirmer |
| « Spark » / « Spark Mail App » | 07:30 | l'application de messagerie Spark (Readdle) | probable |
| « Rogue Belgium » | 39:40 | exemple de fournisseur cité par Nathan | sans importance |
| « FCP », « MCEP », « SkateUp », « Cloud » | divers | Claude Code, MCP, GitHub, Claude | erreurs de transcription |

## Liens

- Original nettoyé : `transcript.md`
- Règles tirées de cette discussion : `../../PRINCIPES.md`
- Plan d'application : `../../GUIDE-DEMARRAGE.md`
