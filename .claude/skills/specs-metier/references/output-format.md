# Format de la spécification finale

La spécification finale doit contenir **exactement ces sections dans cet ordre** :

---

## Sections obligatoires

| # | Section | Contenu |
|---|---------|---------|
| 1 | **Contexte produit** | Pourquoi cette feature existe, dans quel contexte produit |
| 2 | **Problème adressé** | Le problème utilisateur précis que la feature résout |
| 3 | **Promesse utilisateur** | Ce que l'utilisateur peut faire de nouveau ou mieux |
| 4 | **Périmètre de la fonctionnalité** | Dans le scope / Hors scope / Reporté |
| 5 | **Parcours utilisateurs** | Flux principaux (happy path + variantes) |
| 6 | **Structure des interfaces** | Écran par écran — composants, états, interactions |
| 7 | **Indicateurs et règles de calcul** | Définition précise de chaque indicateur affiché |
| 8 | **Règles métier transverses** | Règles s'appliquant à l'ensemble de la feature |
| 9 | **États, erreurs et cas limites** | État vide, chargement, erreurs, edge cases |
| 10 | **Dépendances techniques** | Modules impactés, APIs nécessaires, données requises |
| 11 | **Règles de persistance et snapshots** | Ce qui est persisté, historisé, versionné ou figé |
| 12 | **Événements analytics et critères de succès** | Events, proxys, signaux d'alerte |
| 13 | **Limites assumées et non-objectifs** | Ce que la feature ne fait pas volontairement |
| 14 | **Décisions ouvertes** | Questions restantes à arbitrer par le CPO |

---

## Document de transparence du raisonnement (facultatif)

Produit en complément sur les sujets complexes. Contient :
- Objections formulées par les experts
- Alternatives envisagées
- Arbitrages rendus
- Éléments finalement écartés et justifications
