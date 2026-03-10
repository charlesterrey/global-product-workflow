# Frontières gestion / comptabilité

## Règle fondamentale

> **TerraGrow est un logiciel de pilotage de gestion, non un logiciel de production comptable. Toute feature doit respecter cette frontière.**

---

## Tableau des frontières

| Concept | Vision gestion (TerraGrow) | Vision comptable (hors périmètre direct) |
|---------|---------------------------|------------------------------------------|
| **Résultat** | Solde de gestion prévisionnel ou intermédiaire | Résultat comptable arrêté après clôture |
| **Marge** | Marge brute de gestion sur atelier ou campagne | Marge comptable après retraitements et régularisations |
| **Charge** | Charge de gestion saisie ou importée | Charge comptabilisée, pointée, lettrée |
| **Stock** | Valeur de stock de gestion estimée | Stock comptable valorisé selon méthode officielle |
| **Créance** | Encaissement prévu, flux attendu | Créance comptabilisée et lettrée |
| **Dette** | Décaissement à venir, engagement connu | Dette comptabilisée et rapprochée |

---

## Signal d'alerte

> Si la feature laisse entendre qu'elle produit une **vérité comptable définitive** alors qu'elle exploite des signaux de gestion ou des flux intermédiaires, **corriger immédiatement** le positionnement et le wording.
