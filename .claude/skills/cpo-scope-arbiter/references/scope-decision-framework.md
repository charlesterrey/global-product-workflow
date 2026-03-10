# Framework d'arbitrage du scope

## Grille de décision

| Critère | Must-have | Enrichissement utile | Reporté au futur |
|---------|-----------|---------------------|-----------------|
| **Bloque la valeur de base ?** | Oui — sans ça la feature ne tient pas | Non — la valeur existe sans | Non |
| **Complexité d'implémentation ?** | Acceptable dans la version | Élevée pour le gain apporté | Trop élevée maintenant |
| **Maturité utilisateur ?** | Prêt à absorber | Partiellement prêt | Pas encore prêt |
| **Dépendance bloquante ?** | Aucune dépendance non résolue | Dépendance connue et planifiée | Dépendance non résolue |
| **Cohérence avec la version cible ?** | Aligné | Aligné mais en marge | Hors périmètre de version |

---

## Les 3 risques à corriger en priorité

| Risque | Description | Action |
|--------|-------------|--------|
| **Sur-promesse** | La spec laisse entendre que TerraGrow fait plus qu'il ne fait | Corriger le wording |
| **Sous-spécification** | Des règles critiques ne sont pas encore définies | Bloquer la livraison |
| **Sur-spécification** | Des raffinements non utiles à la version alourdissent la spec | Déplacer dans « futur » |
