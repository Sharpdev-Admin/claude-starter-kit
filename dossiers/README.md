# dossiers/ — une fiche par personne ou entité

Patients, clients, fournisseurs, partenaires : chacun a **une fiche**, et une seule, rangée par
type :

```
dossiers/
├── patients/     <slug>.md
├── clients/      <slug>.md
├── fournisseurs/ <slug>.md
└── partenaires/  <slug>.md
```

Claude crée les sous-dossiers au besoin ; renomme-les si tes activités ont d'autres catégories.

## Ce qu'une fiche contient, et ne contient pas

- **Contient** : qui c'est, comment le joindre, ce qui est en cours (demandes ouvertes, urgence,
  prochaine action), et un historique daté des interactions.
- **Référence** ses ressources (`../../ressources/...`) : le mail, le résultat d'examen, la
  facture. Elle ne les copie pas. Si tu veux le détail, tu ouvres la ressource.
- **Ne contient jamais** un mot de passe ou une donnée que tu n'écrirais pas dans un dossier
  papier laissé sur un bureau.

Modèle : `_template-fiche-dossier.md`. Pour un patient, pense au secret médical : le repo est
privé, mais réfléchis à ce que tu y mets (initiales ou numéro de dossier plutôt que nom complet,
par exemple). Demande à Claude d'appliquer la règle que tu choisis partout.
