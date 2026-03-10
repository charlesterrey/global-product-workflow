# Framework de définition des événements analytics

## Structure de définition d'un événement

```
DÉFINITION D'UN ÉVÉNEMENT ANALYTICS
─────────────────────────────────────

Nom de l'événement  : [verbe_objet en snake_case]
                      Exemples : feature_viewed, alert_clicked,
                                 indicator_expanded, export_triggered

Déclenché quand     : [condition précise]

Propriétés à capturer :
  - user_role        : [conseiller | agriculteur | admin]
  - exploitation_id  : [identifiant anonymisé]
  - campaign_year    : [année de campagne]
  - [propriété spécifique à la feature]

Type de signal      : [ ] Activation  [ ] Engagement  [ ] Rétention

Vanity metric à éviter : [ce qu'il ne faut PAS mesurer ici]
```

---

## Grille d'évaluation des métriques

| Type de métrique | Définition | Exemple TerraGrow | Priorité |
|-----------------|-----------|-------------------|---------|
| **Proxy d'activation** | Première action significative prouvant que l'utilisateur a compris la valeur | Première projection de trésorerie créée | Haute |
| **Proxy d'engagement** | Action répétée prouvant l'utilisation régulière | Retour sur la feature dans les 7 jours suivants | Haute |
| **Proxy de rétention** | Usage maintenu sur une période longue | Feature utilisée sur 3 campagnes consécutives | Haute |
| **Signal d'alerte** | Indicateur que la feature ne crée pas de valeur | Taux d'ouverture de l'écran < 10% des utilisateurs | Critique |
| **Vanity metric** | Métrique flatteuse mais non actionnable | Nombre de pages vues total | À éviter |
