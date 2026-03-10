# Règles de gestion des périodes et de la temporalité comptable

## Questions systématiques

À appliquer sur toute feature manipulant des données temporelles :

1. Cette feature **mélange-t-elle des données de campagnes différentes** sans le signaler ?
2. Distingue-t-elle explicitement les données **avant clôture** (provisoires) et **après clôture** (révisées) ?
3. Que se passe-t-il une fois la campagne et l'exercice clos ? Que doit-on **figer** ? Que peut-on **recalculer** ?
4. Les **charges constatées d'avance** et les **produits à recevoir** sont-ils traités correctement ?
5. Les **décalages de comptabilisation** (facture reçue ≠ charge économique réelle) sont-ils explicités ?
6. Les **snapshots mensuels ou annuels** sont-ils prévus pour préserver la photographie d'états antérieurs ?

---

## Règle sur les référentiels RICA et ANC

> Si la logique s'appuie sur ces standards, vérifier que le niveau de traduction dans le produit reste fidèle **sans promettre une conformité totale**. Utiliser une terminologie neutre si TerraGrow ne fait qu'emprunter la logique sans certifier la conformité.
