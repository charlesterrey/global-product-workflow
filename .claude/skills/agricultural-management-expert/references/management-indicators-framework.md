# Grille d'évaluation des indicateurs de gestion

## Questions systématiques par indicateur

Pour chaque indicateur affiché ou calculé dans la feature, appliquer les 4 questions suivantes :

| Question | Ce qu'on évalue | Signal d'alerte |
|----------|----------------|-----------------|
| Est-ce un indicateur réellement utile au pilotage ? | Aide-t-il à détecter une tension, à anticiper, à prioriser une intervention ? | Non → l'indicateur est décoratif ou « fait expert » sans aider à agir |
| Est-ce qu'il est compréhensible par l'utilisateur visé ? | Le conseiller ou l'agriculteur peut-il l'interpréter sans formation spécifique ? | Non → risque de mauvaise utilisation ou de perte de confiance dans le produit |
| Est-ce qu'il est actionnable ou seulement descriptif ? | Permet-il de déclencher une action concrète ou ne fait-il que constater ? | Seulement descriptif → vérifier si le produit donne un levier en complément |
| Peut-il être mal interprété sans explication ? | Existe-t-il une confusion possible avec un autre concept ou un autre usage ? | Oui → ajouter une définition courte ou une info-bulle dans la spec |

---

## Leviers d'action disponibles en conseil de gestion agricole

Face à une tension détectée, vérifier si la feature permet d'activer au moins l'un des leviers suivants :

- **Rythme des dépenses** — décalage ou réétalement d'un achat ou d'une charge
- **Négociation fournisseur** — délai de paiement, regroupement de commandes
- **Anticipation de financement** — mobilisation d'une ligne de crédit, déclenchement d'un emprunt court terme
- **Priorisation du conseil** — aide à identifier quelle exploitation traiter en premier dans un portefeuille
- **Revue d'un atelier** — remise en question d'un itinéraire ou d'une allocation de charges
- **Mise à jour d'une hypothèse** — actualisation d'un rendement, d'un prix de vente ou d'un coût
- **Déclenchement d'un rendez-vous** — alerte suffisamment tôt pour intervenir avant la crise

> **Règle :** Si la feature révèle un problème mais ne donne aucun levier ou ne prépare aucune action, le signaler explicitement dans la sortie.

---

## Temporalité et cycles de décision

Vérifier que la feature intervient au bon moment du cycle :

| Cycle | Moment clé | Ce que la feature doit permettre |
|-------|-----------|----------------------------------|
| Cycle de trésorerie | Tension prévisible 4-6 semaines avant l'échéance | Alerte précoce, pas un constat post-crise |
| Cycle de campagne | Avant les engagements d'intrants (semences, engrais) | Projection et arbitrage avant achat |
| Cycle de conseil | Avant les rendez-vous récurrents du conseiller | Matière préparée pour le RDV, pas après |
| Cycle annuel | Avant clôture d'exercice | Vérification de cohérence, pas révision tardive |
