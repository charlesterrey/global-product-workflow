# Exemple — Document Word : Marges par Culture

## Page de couverture

| Champ | Contenu |
|-------|---------|
| Titre | Dashboard Marges par Culture |
| Produit | TerraGrow |
| Type | Design Specification |
| Date | 2026-03-05 |
| Auteur | Équipe Produit |
| Version | 1.0 |

---

## Table des matières

1. Contexte Produit
2. Objectifs de la fonctionnalité
3. Vue d'ensemble
4. Parcours utilisateur
5. Structure de la page
6. Composants UI
7. Indicateurs métier affichés
8. Logique métier
9. Cas d'usage
10. États de l'interface
11. Sources de données
12. Analytics produit
13. Contribution des expertises métiers
14. Issues Linear

---

## 1. Contexte Produit

Le dashboard **Marges par Culture** permet aux conseillers de gestion et experts-comptables agricoles de visualiser la rentabilité de chaque culture d'une exploitation.

Ce tableau de bord est développé pour répondre au besoin de **pilotage économique par culture**, actuellement réalisé manuellement via des tableaux Excel.

---

## 2. Objectifs de la fonctionnalité

**Problèmes résolus :**
- Difficulté à comparer les marges entre cultures
- Absence de vision consolidée charges/produits par culture
- Temps de calcul manuel excessif

**Utilisateurs concernés :**
- Conseillers de gestion agricole
- Experts-comptables agricoles
- Exploitants agricoles (consultation)

---

## 3. Vue d'ensemble

```
Sélection campagne → Affichage indicateurs clés → Tableau détaillé par culture → Graphique comparatif → Export
```

L'utilisateur sélectionne une campagne, visualise les indicateurs de synthèse, explore le détail par culture dans un tableau interactif, et peut exporter les résultats.

---

## 4. Parcours utilisateur

1. L'utilisateur accède au menu **Analyses économiques > Marges par culture**
2. Il sélectionne la campagne (année)
3. Le dashboard affiche les indicateurs clés en haut de page
4. Le tableau détaillé liste chaque culture avec ses marges
5. Le graphique barre compare les marges brutes par culture
6. L'utilisateur peut filtrer par type de culture ou trier le tableau
7. Il exporte le tableau au format Excel ou PDF

---

## 5. Structure de la page

### Header
- Titre : "Marges par Culture"
- Sélecteur de campagne
- Bouton d'export

### Indicateurs clés (KPI cards)
- Marge brute totale
- Marge brute moyenne / ha
- Culture la plus rentable
- Culture la moins rentable

### Graphique
- Bar chart horizontal : marge brute par culture (triée décroissante)

### Tableau détaillé
- Colonnes : Culture | Surface (ha) | Produit (€) | Charges opé (€) | Marge brute (€) | Marge brute/ha (€/ha)
- Tri et filtre sur chaque colonne

### Bloc analyse
- Zone de texte : analyse automatique des points saillants

---

## 6. Composants UI

| Composant | Description | Interaction |
|-----------|-------------|-------------|
| CampaignSelector | Dropdown de sélection campagne | Recharge les données |
| KPICard | Carte indicateur clé | Affichage seul |
| BarChart | Graphique barre horizontale | Hover tooltip |
| DataTable | Tableau trié/filtrable | Tri, filtre, pagination |
| ExportButton | Bouton d'export Excel/PDF | Clic → téléchargement |
| AnalysisBlock | Zone texte analyse | Affichage seul |

---

## 7. Indicateurs métier affichés

| Indicateur | Description | Utilité |
|------------|-------------|---------|
| Marge brute totale | Somme des marges brutes de toutes les cultures | Vision globale exploitation |
| Marge brute / ha | Marge brute divisée par la surface | Comparaison entre cultures |
| Produit total | Chiffre d'affaires par culture | Évaluer le revenu |
| Charges opérationnelles | Semences + engrais + phytos + mécanisation | Identifier les postes de coûts |
| Rendement moyen | Quantité produite / ha | Contexte agronomique |

---

## 8. Logique métier

```
marge_brute = produit_total – charges_operationnelles
marge_brute_ha = marge_brute / surface_ha
produit_total = rendement × prix_vente + aides_couplées
charges_operationnelles = semences + engrais + phytosanitaires + mécanisation
```

**Règles :**
- Les aides PAC découplées ne sont **pas** intégrées dans la marge brute
- Les charges de mécanisation sont réparties au prorata des heures par culture
- Les surfaces sont en hectares, arrondies à 2 décimales

---

## 9. Cas d'usage

**Cas 1 — Conseiller de gestion**
Un conseiller analyse le portefeuille d'un exploitant céréalier. Il constate que le colza affiche une marge brute/ha de 280 €/ha contre 520 €/ha pour le blé tendre. Il recommande d'évaluer l'intérêt agronomique du colza vs une alternative.

**Cas 2 — Expert-comptable**
Un expert-comptable vérifie que les charges de mécanisation sont correctement ventilées entre cultures avant la clôture comptable.

---

## 10. États de l'interface

| État | Comportement |
|------|-------------|
| Loading | Skeleton des KPI cards + tableau |
| Pas de données | Message "Aucune donnée pour cette campagne" + suggestion |
| Erreur | Bandeau d'erreur + bouton réessayer |
| Données partielles | Affichage avec mention "[Données incomplètes]" sur les cultures concernées |

---

## 11. Sources de données

| Donnée | Source | Fréquence |
|--------|--------|-----------|
| Surfaces | Déclaration PAC / saisie manuelle | Annuelle |
| Rendements | Saisie récolte | Annuelle |
| Prix de vente | Saisie ou import négoce | Annuelle |
| Charges opé | Comptabilité analytique | Continue |
| Aides couplées | Import ASP | Annuelle |

---

## 12. Analytics produit

| Événement | Déclencheur |
|-----------|-------------|
| `page_viewed` | Ouverture du dashboard |
| `campaign_selected` | Changement de campagne |
| `filter_used` | Application d'un filtre tableau |
| `sort_applied` | Tri d'une colonne |
| `export_clicked` | Clic sur export |
| `chart_hovered` | Survol d'une barre du graphique |

---

## 13. Contribution des expertises métiers

**Expert-Comptable :**
- Validation de la répartition des charges de mécanisation (clé analytique heures/ha)
- Conformité du traitement des aides PAC (produit vs subvention d'exploitation)

**Conseiller de Gestion :**
- Benchmarking des marges brutes par culture vs référentiels régionaux
- Identification des exploitations sous-performantes par culture

**Agronome :**
- Contexte rendement : potentiel pédoclimatique vs rendement réalisé
- Impact des itinéraires techniques sur la marge

---

## 14. Issues Linear

| Titre | Description |
|-------|-------------|
| [TERRA-301] Dashboard Marges Culture — Structure page | Layout, header, KPI cards, zones graphique et tableau |
| [TERRA-302] Composant KPICard — Marges | 4 cartes indicateurs avec calcul dynamique |
| [TERRA-303] BarChart — Marges par culture | Graphique barre horizontale trié, tooltip |
| [TERRA-304] DataTable — Détail par culture | Tableau trié/filtrable avec colonnes marges |
| [TERRA-305] Logique calcul marges | Service de calcul marge brute et marge/ha |
| [TERRA-306] Export Excel/PDF | Génération du fichier d'export |
| [TERRA-307] États vides et erreurs | Gestion loading, empty state, erreur |
| [TERRA-308] Analytics tracking | Implémentation des événements |
