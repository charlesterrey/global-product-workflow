# Questions systématiques d'analyse du modèle de données

## Questions à appliquer sur chaque feature

À appliquer avant de valider la faisabilité data :

1. Quelles **entités** sont créées, modifiées ou supprimées par cette feature ?
2. Quelles sont les **sources de vérité** pour chaque donnée affichée ou calculée ?
3. Quels champs sont **calculés dynamiquement** vs **persistés en base** ?
4. Quels modules existants lisent les mêmes entités et pourraient être **affectés** ?
5. Les **relations entre entités** sont-elles correctement définies (1-1, 1-N, N-N) ?
6. Les **mappings avec des données externes** (imports comptables, données agronomiques) sont-ils explicités ?
7. Les **droits d'accès** et les règles de visibilité sont-ils définis par entité ?

---

## Matrice de persistance

À compléter pour chaque feature :

| Donnée | Source | Persiste ? | Recalculable ? | Historisée ? | Figée après clôture ? |
|--------|--------|-----------|----------------|-------------|----------------------|
| [Nom donnée 1] | [Source] | Oui / Non | Oui / Non | Oui / Non | Oui / Non |
| [Nom donnée 2] | [Source] | Oui / Non | Oui / Non | Oui / Non | Oui / Non |
| [Nom donnée 3] | [Source] | Oui / Non | Oui / Non | Oui / Non | Oui / Non |
