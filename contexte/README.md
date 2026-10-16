# contexte/ — qui tu es, pour Claude

Claude lit ce dossier au début de chaque session. C'est ce qui fait qu'il travaille pour **toi** et
pas pour un utilisateur générique. Trois fichiers, remplis avec Claude lors de la première session
(`PROMPT-INSTALLATION.md`) :

| Fichier | Contenu |
|---|---|
| `activites.md` | Tes activités, leurs adresses mail, leurs catégories de demandes, leurs outils. |
| `style-de-reponse.md` | Comment tu réponds : ton, langue, formules, ce que tu promets et ne promets jamais. Claude l'enrichit en observant tes vrais envois. |
| `niveau-de-confiance.md` | Jusqu'où Claude peut aller tout seul, par activité et par catégorie. **Toi seul modifies ce fichier.** |

Quand tu changes d'avis sur l'un de ces points, dis-le à Claude en session : il met le fichier à
jour, et la leçon part dans `tasks/lessons.md` au `EOS`.
