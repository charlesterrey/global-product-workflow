# Checklist complète de revue d'implémentation

Parcourir systématiquement chaque catégorie avant de valider la spec comme buildable :

---

## Checklist

| Catégorie | Éléments à vérifier |
|-----------|-------------------|
| **États de l'interface** | État initial (premier chargement), état vide (pas de données), état de chargement, état d'erreur réseau, état d'erreur métier, état de succès après action |
| **Permissions et accès** | Qui peut voir cet écran ? Qui peut effectuer chaque action ? Que voit un utilisateur sans droit ? |
| **Ordre de priorité entre règles** | Si deux règles s'appliquent simultanément, laquelle prime ? L'ordre est-il explicite ? |
| **Données partielles** | Que se passe-t-il si une donnée requise est absente, nulle ou incohérente ? |
| **Cas multi-comptes** | Le comportement est-il identique pour tous les types de comptes ? Exceptions ? |
| **Champs obligatoires** | Quels champs sont requis ? Quel message d'erreur si absent ? |
| **Logique de report** | Si une action échoue, que se passe-t-il ? Retry automatique ? Message utilisateur ? |
| **Effets d'une suppression** | Si un objet est supprimé, que se passe-t-il pour les données qui en dépendent ? |
| **Cohérence graphique/tableau** | Si un graphique et un tableau affichent les mêmes données, sont-ils strictement synchronisés ? |
| **Contrats API** | Quels endpoints sont nécessaires ? Quelles sont les structures de requête et réponse ? |
| **Feature flags** | La feature doit-elle être déployable partiellement ou progressivement ? |
| **Observabilité** | Quels logs, métriques ou traces sont nécessaires pour déboguer en production ? |
| **Critères de done** | La feature est-elle done quand ? (tests passants, performance OK, analytics instrumenté, etc.) |
