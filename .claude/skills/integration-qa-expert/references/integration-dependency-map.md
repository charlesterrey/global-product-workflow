# Cartographie des dépendances inter-modules

## Framework d'analyse des dépendances

Pour chaque feature, identifier et documenter les dépendances selon ces catégories :

| Type de dépendance | Questions à poser | Impact si non géré |
|-------------------|-------------------|-------------------|
| **Données en lecture** | Quelles données d'autres modules cette feature affiche-t-elle ? Ces données peuvent-elles changer sans que cette feature le sache ? | Affichage de données obsolètes ou incohérentes |
| **Données en écriture** | Cette feature modifie-t-elle des données lues par d'autres modules ? | Effets de bord silencieux sur d'autres vues |
| **Événements déclenchés** | Cette feature émet-elle des événements ou des notifications vers d'autres parties du système ? | Événements manquants ou doublonnés |
| **Données externes** | Cette feature dépend-elle de données importées (comptable, agronomique, météo) ? | Point de défaillance externe non géré |
| **Calculs partagés** | Cette feature utilise-t-elle des règles de calcul définies ailleurs dans le système ? | Divergence si la règle source est modifiée |

---

## Template de cartographie à compléter

```
CARTOGRAPHIE DES DÉPENDANCES — [Nom de la feature]
────────────────────────────────────────────────────
Modules en lecture  : [liste des modules lus]
Modules en écriture : [liste des modules modifiés]
Événements émis     : [liste des événements produits]
Sources externes    : [liste des sources externes]
Calculs partagés    : [règles partagées avec d'autres features]
```
