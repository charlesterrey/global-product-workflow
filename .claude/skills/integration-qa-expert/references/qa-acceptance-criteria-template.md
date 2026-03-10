# Template de critères d'acceptance et cas de test

Structure à compléter pour chaque feature avant de la considérer comme livrable :

---

## Template

```
CRITÈRES D'ACCEPTANCE — [Nom de la feature]
─────────────────────────────────────────────

Cas nominal (happy path) :
  ÉTANT DONNÉ [contexte initial]
  QUAND [action utilisateur ou événement]
  ALORS [résultat attendu]

Cas limites à tester :
  [ ] Données manquantes ou partielles
  [ ] Valeurs extrêmes (zéro, négatif, très grand)
  [ ] Utilisateur sans les droits requis
  [ ] Perte de connexion en cours d'action
  [ ] Données incohérentes entre modules

Tests de non-régression :
  [ ] [Feature existante 1] — comportement inchangé
  [ ] [Feature existante 2] — comportement inchangé

Critères de performance :
  Temps de chargement : < [X] ms
  Volumétrie testée   : [N] exploitations / [N] années

Critère de done complet :
  [ ] Tests unitaires passants
  [ ] Tests d'intégration passants
  [ ] Analytics instrumenté
  [ ] Documentation technique mise à jour
  [ ] Revue code approuvée
```
