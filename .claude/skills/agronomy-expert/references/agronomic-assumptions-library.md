# Bibliothèque des hypothèses et variables agronomiques

## Variables de contexte à rendre visibles

Pour chaque feature impliquant des données techniques, identifier lesquelles de ces variables de contexte majeures la feature doit **afficher**, **supposer** ou **ignorer explicitement** :

- Type de sol et capacité de rétention en eau
- Zone climatique et historique des aléas (gel, sécheresse, excès pluviométrie)
- Historique cultural de la parcelle (rotations, précédents culturaux)
- Pression sanitaire locale (maladies, ravageurs, adventices)
- Accès à l'irrigation et type de système
- Itinéraire technique choisi (intensif, raisonné, bio)
- Variété ou race sélectionnée et ses performances attendues
- Stratégie de fertilisation (type, doses, fractionnement)
- Qualité d'exécution opérationnelle (matériel, timing des interventions)

---

## Grille de validation des hypothèses techniques

| Hypothèse | Conditions de validité | Risque si ignoré |
|-----------|----------------------|------------------|
| Rendement moyen | Valable uniquement pour un type de sol + zone climatique + variété donnés | Fausse précision si présenté comme universel |
| Dose d'intrant standard | Dépend de l'objectif de rendement, de l'analyse de sol et de la pression sanitaire | Sous ou sur-dosage si appliqué sans contexte |
| Date d'intervention | Très variable selon zone géographique et millésime climatique | Décalage réel possible de 2-6 semaines |
| Coût de production moyen | Dépend de la structure de charges, du niveau de mécanisation, de la taille de l'exploitation | Écart de 20-40% selon exploitation |
| Linéarité des consommations | Les achats d'intrants sont saisonniers et irréguliers, pas linéaires | Trésorerie faussée si lissée sur 12 mois |

---

## Mailles de représentation

| Maille | Pertinente pour | Risque d'une mauvaise maille |
|--------|----------------|------------------------------|
| **Parcelle** | Agronomie fine, rotation, historique cultural | Trop granulaire pour la gestion économique globale |
| **Atelier** | Analyse technico-économique par production | Confusion si les ateliers partagent des charges mécanisation |
| **Exploitation** | Vision globale trésorerie et rentabilité | Masque les déséquilibres entre ateliers |
