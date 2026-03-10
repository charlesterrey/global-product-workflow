# Bibliothèque des edge cases fréquents dans TerraGrow

Edge cases récurrents à vérifier systématiquement pour toute feature financière ou de gestion :

---

## Edge cases à tester

| # | Edge case | Question à résoudre |
|---|-----------|-------------------|
| 1 | **Zéro saisie** | Exploitation avec zéro saisie sur la période — que s'affiche-t-il ? |
| 2 | **Données N non disponibles** | Données de l'année N non encore disponibles mais interface en N+1 — comportement ? |
| 3 | **Valeurs négatives** | Valeurs négatives dans un calcul attendu positif — gestion visuelle et logique |
| 4 | **Division par zéro** | Division par zéro dans un ratio ou un indicateur — fallback défini ? |
| 5 | **Changement de campagne en cours** | Changement de campagne en cours de saisie — impact sur les calculs en cours |
| 6 | **Import format différent** | Données importées d'un outil tiers avec un format différent — règle de réconciliation |
| 7 | **Multi-exploitations** | Utilisateur avec plusieurs exploitations — filtre et portée des calculs |
| 8 | **Modification rétroactive** | Modification rétroactive d'une saisie passée — impact sur les historiques et snapshots |
| 9 | **Fuseau horaire** | Dates de clôture, de campagne et d'alerte sont-elles timezone-safe ? |
| 10 | **Export / impression** | Les données affichées sont-elles fidèlement reproduites à l'export ? |
