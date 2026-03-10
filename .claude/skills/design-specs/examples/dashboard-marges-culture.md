# Exemple — Design Spec : Dashboard Marges par Culture

## Brief CPO d'entree

> **Feature :** Dashboard Marges par Culture
>
> **Probleme :** Le conseiller ouvre 8 fiches culture une par une pour comparer les marges. Ca prend 20 min avant chaque RDV. Il n'a pas de vue synthetique.
>
> **Solution :** Une page qui affiche toutes les marges brutes de toutes les cultures d'un coup, avec comparaison N-1 et references sectorielles CER.
>
> **Utilisateur :** Conseiller de gestion — usage hebdomadaire (avant RDV), expert-comptable — usage mensuel
>
> **Peut faire :** Comparer marges par culture, voir evolution N-1, comparer aux references, identifier les cultures sous-performantes, cliquer pour detail culture
>
> **Ne fait pas :** Export Excel (v2), simulation de prix (v2), IFT par parcelle (donnees pas disponibles)
>
> **Donnees dispo :** Comptabilite analytique par culture, surfaces, rendements, prix de vente. References CER via API.

---

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DOCUMENT 1 — SPEC DESIGN
Dashboard Marges par Culture — v2025-03
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 1. Contexte & Probleme resolu

**Situation actuelle :** Le conseiller de gestion ouvre les fiches culture une par une dans TerraGrow pour comparer les marges. Avec 5 a 8 cultures par exploitation, ca prend 15 a 20 minutes de navigation avant chaque RDV client. Il n'a aucune vue comparative et doit mentalement aggreger les chiffres.

**Ce que TerraGrow apporte :** Une vue synthetique qui affiche toutes les marges brutes de toutes les cultures sur une seule page, avec comparaison N-1 et references sectorielles CER. Le conseiller identifie en moins de 2 minutes quelle culture pose probleme et peut préparer son conseil.

**Utilisateur cible :** Conseiller de gestion (principal) — hebdomadaire avant RDV. Expert-comptable (secondaire) — mensuel en periode de cloture.

**Impact metier :** Preparation du RDV passe de 20 min a 5 min. Le conseiller peut se concentrer sur le conseil plutot que sur la collecte de chiffres. Identification immediate des cultures en derive.

---

## 2. User Stories

**US-1** | En tant que conseiller de gestion, je veux voir les marges brutes de toutes les cultures d'une exploitation sur une seule page afin de preparer mon RDV en 5 minutes au lieu de 20.
> Contexte : Le conseiller a un RDV avec l'agriculteur Dupont le lendemain. Il ouvre TerraGrow, selectionne l'exploitation, et veut immediatement identifier les cultures qui ont sous-performe cette campagne pour orienter la discussion.

**US-2** | En tant que conseiller de gestion, je veux comparer les marges de la campagne actuelle avec N-1 afin de detecter les derives et expliquer les ecarts a l'agriculteur.
> Contexte : La campagne ble tendre 2024 affiche une marge brute de 180 EUR/ha, contre 290 EUR/ha en 2023. Le conseiller veut comprendre si c'est le prix, le rendement ou les charges qui ont derive pour construire son argumentaire de conseil.

**US-3** | En tant que conseiller de gestion, je veux comparer les marges de l'exploitation avec les references sectorielles CER afin de situer la performance de l'agriculteur par rapport au marche.
> Contexte : L'agriculteur pense que ses marges colza sont bonnes. Le conseiller veut montrer que la marge de 280 EUR/ha est en realite 15% sous la reference CER regionale (330 EUR/ha) pour declencher une action corrective.

**US-4** | En tant que conseiller de gestion, je veux identifier visuellement les cultures en alerte rouge afin de prioriser mon conseil sans lire chaque ligne du tableau.
> Contexte : Le conseiller a 45 minutes de RDV. Il doit aller directement aux cultures qui posent probleme. Un code couleur clair lui permet d'identifier les 2-3 cultures prioritaires en quelques secondes.

**US-5** | En tant que conseiller de gestion, je veux cliquer sur une culture pour acceder au detail de ses charges afin de comprendre quels postes expliquent une marge degradee.
> Contexte : La marge tournesol est rouge. Le conseiller clique pour voir si c'est les charges de mecanisation, les intrants, ou le prix de vente qui est en cause avant de formuler une recommandation.

---

## 3. Ce qu'on peut faire / Ce qu'on NE FAIT PAS

✅ CE QU'ON PEUT FAIRE
- Voir les marges brutes EUR/ha de toutes les cultures sur une campagne
- Basculer l'affichage avec comparaison N-1 (toggle)
- Activer les references CER regionales (toggle)
- Identifier les cultures en alerte via code couleur automatique
- Trier le tableau par marge, surface, ecart N-1
- Cliquer sur une culture pour acceder a la fiche detail
- Changer la campagne via un dropdown

🚫 CE QU'ON NE FAIT PAS (dans cette version)
- Export Excel ou PDF — prevu v2 (demande identifiee mais non prioritaire)
- Simulation de prix ou de rendement — complexite metier, v2
- IFT (Indice de Frequence de Traitement) par parcelle — donnees pas encore disponibles dans TerraGrow
- Comparaison multi-exploitations — feature portefeuille, scope different

---

## 4. User Journey par ecran

**JOURNEY — "Conseiller prepare son RDV avec l'agriculteur Dupont"**

Etape 1 — Acces a la page
  → Ce que l'user voit : Page chargee avec le nom de l'exploitation en header, campagne selectionnee par defaut (campagne en cours), tableau des cultures avec marges brutes EUR/ha, graphique a barres horizontales
  → Action disponible : Changer l'exploitation (dropdown), changer la campagne (dropdown)
  → Resultat : Donnees de l'exploitation selectionnee chargees

Etape 2 — Lecture des alertes
  → Ce que l'user voit : 2 cultures en rouge (marge < 80% reference), 1 en orange (80-100%), 5 en vert. KPIs en haut : marge totale, marge moyenne, nb cultures, variation N-1 globale
  → Action disponible : Identifier visuellement les cultures problematiques
  → Resultat : Le conseiller repere immediatement ble tendre et tournesol en rouge

Etape 3 — Activation comparaison N-1
  → Ce que l'user voit : Toggle "Comparer N-1" — inactif par defaut
  → Action disponible : Activer le toggle
  → Resultat : Colonne "Var N-1" apparait dans le tableau, barres groupees sur le graphique (2024 vs 2023), couleur secondaire pour N-1

Etape 4 — Activation references CER
  → Ce que l'user voit : Toggle "References CER" — inactif par defaut
  → Action disponible : Activer le toggle
  → Resultat : Ligne de reference verticale sur le graphique, colonne "vs Ref" dans le tableau, seuil de 80% indique

Etape 5 — Investigation culture en alerte
  → Ce que l'user voit : Ligne "Ble tendre" en rouge dans le tableau, curseur pointer au survol
  → Action disponible : Cliquer sur la ligne
  → Resultat : Navigation vers la fiche detail culture ble tendre avec decomposition des charges

ETATS PARTICULIERS
- Etat vide (aucune culture) : Message "Aucune culture renseignee pour cette campagne" + bouton CTA "Ajouter une culture"
- Etat erreur API references CER : Bandeau non bloquant "References CER temporairement indisponibles" — le reste de la page fonctionne
- Etat chargement : Skeleton loaders sur le graphique et le tableau, KPIs en gris
- Etat donnees partielles : Mention "(incomplet)" en italique a cote du nom culture, tooltip explicatif au survol

---

## 5. Structure & Composants de la page

**STRUCTURE DE LA PAGE**

[Header] : Nom exploitation (breadcrumb), dropdown campagne, toggles "N-1" et "References CER"

[KPIs synthese] : 4 cards — Marge brute totale (EUR), Marge brute moyenne (EUR/ha), Nb cultures, Variation vs N-1 (%)

[Graphique comparatif] : Bar chart horizontal, cultures en Y, marge EUR/ha en X. Couleurs : vert > reference, orange 80-100%, rouge < 80%. Ligne reference verticale si toggle actif.

[Tableau detaille] : Colonnes — Culture | Surface (ha) | Rendement (q/ha) | Marge brute/ha | Marge totale (EUR) | Var N-1 | vs Ref. Tri cliquable. Clic ligne → fiche culture.

**COMPOSANTS FIGMA**

| Composant            | Usage                         | DS existant | Interactions cles              |
|----------------------|-------------------------------|-------------|--------------------------------|
| KPI Card             | 4 indicateurs synthese        | Oui         | —                              |
| Bar Chart Horizontal | Comparaison marges cultures   | Oui         | Hover tooltip, toggle N-1      |
| Data Table sortable  | Tableau detaille cultures     | Oui         | Tri colonnes, clic ligne       |
| Toggle Switch        | N-1 / References CER          | Oui         | On/off avec transition         |
| Alert Badge          | Indicateur rouge/orange/vert  | A creer     | Tooltip explication seuil      |
| Skeleton Loader      | Etat chargement               | Oui         | Animation pulse                |

**LIBERTE DU DESIGNER**

✅ Peut optimiser : layout, espacements, micro-animations, couleurs dans le DS, ordre des colonnes secondaires, style du tooltip
🚫 Ne doit PAS changer : seuils de couleur (80% et 100% de la reference), libelles des indicateurs (marge brute, surface, rendement), ordre des sections (KPIs avant graphique avant tableau)


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DOCUMENT 2 — ISSUES LINEAR
Dashboard Marges par Culture — 5 issues
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

═══════════════════════════════════════════════════
ISSUE — Affichage comparatif des marges brutes par culture
Priorite : Critique
Type : Full-stack
═══════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux voir les marges brutes de toutes les cultures sur une seule page afin de preparer mon RDV en 5 minutes.

CONTEXTE
Le conseiller passe aujourd'hui 20 min a naviguer entre les fiches culture pour aggreger les chiffres. Cette issue est le coeur du dashboard : sans elle, aucune autre fonctionnalite n'a de sens.

CRITERES D'ACCEPTATION
- [ ] La page affiche toutes les cultures de l'exploitation pour la campagne selectionnee
- [ ] Chaque culture affiche : surface (ha), rendement (q/ha), marge brute/ha (EUR), marge totale (EUR)
- [ ] Un dropdown permet de changer la campagne (toutes les campagnes disponibles)
- [ ] Les KPIs synthese sont calcules et affiches : marge totale, marge moyenne, nb cultures
- [ ] Si aucune culture : message vide + CTA "Ajouter une culture"
- [ ] Temps de chargement < 2 secondes pour < 20 cultures

DEFINITION OF DONE
- [ ] Design Figma livre et valide CPO
- [ ] Implementation conforme au design
- [ ] Etats vide / erreur / chargement implementes
- [ ] Review code effectuee
- [ ] Teste sur les donnees de staging
- [ ] Merge sur main

═══════════════════════════════════════════════════
ISSUE — Comparaison N-1 sur les marges
Priorite : Haute
Type : Front
═══════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux comparer les marges avec N-1 afin de detecter les derives et expliquer les ecarts a l'agriculteur.

CONTEXTE
Les conseillers utilisent systematiquement la comparaison annuelle lors des RDV. C'est le principal outil de detection des derives. La colonne N-1 et le toggle sont des features tres demandees.

CRITERES D'ACCEPTATION
- [ ] Un toggle "Comparer N-1" est present et desactive par defaut
- [ ] A l'activation : colonne "Var N-1" apparait dans le tableau (% et EUR)
- [ ] A l'activation : le graphique passe en barres groupees (N et N-1)
- [ ] Si N-1 indisponible pour une culture : afficher "—" et tooltip "Donnee N-1 non disponible"
- [ ] Le toggle conserve son etat lors d'un changement de campagne

DEFINITION OF DONE
- [ ] Design Figma livre et valide CPO
- [ ] Implementation conforme au design
- [ ] Etats vide / erreur / chargement implementes
- [ ] Review code effectuee
- [ ] Teste sur les donnees de staging
- [ ] Merge sur main

═══════════════════════════════════════════════════
ISSUE — Integration references sectorielles CER
Priorite : Haute
Type : Full-stack
═══════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux comparer les marges avec les references CER afin de situer la performance par rapport au marche.

CONTEXTE
Les references CER sont l'outil de benchmarking standard utilise par les conseillers agricoles en France. Montrer l'ecart a la reference est souvent le declencheur du conseil. L'API CER doit etre consommee en backend.

CRITERES D'ACCEPTATION
- [ ] Un toggle "References CER" est present et desactive par defaut
- [ ] A l'activation : ligne de reference verticale sur le graphique
- [ ] A l'activation : colonne "vs Ref" dans le tableau (% d'ecart)
- [ ] Code couleur automatique : vert si marge > reference, orange si 80-100%, rouge si < 80%
- [ ] Si API CER indisponible : bandeau non bloquant, toggle desactive avec message explicatif
- [ ] Les references sont filtrees par region et par type de culture

DEFINITION OF DONE
- [ ] Design Figma livre et valide CPO
- [ ] Implementation conforme au design
- [ ] Etats vide / erreur / chargement implementes
- [ ] Review code effectuee
- [ ] Teste sur les donnees de staging
- [ ] Merge sur main

═══════════════════════════════════════════════════
ISSUE — Tri et navigation vers fiche culture
Priorite : Normale
Type : Front
═══════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux trier le tableau et cliquer sur une culture pour acceder au detail afin de comprendre les postes de charges qui expliquent une marge degradee.

CONTEXTE
Apres avoir identifie une culture en alerte, le conseiller veut comprendre pourquoi. La navigation vers la fiche culture existante est le point d'entree naturel. Le tri permet de prioriser rapidement.

CRITERES D'ACCEPTATION
- [ ] Toutes les colonnes du tableau sont triables (clic sur en-tete)
- [ ] Le tri actif est indique visuellement (icone fleche)
- [ ] Tri par defaut : marge brute/ha decroissant
- [ ] Clic sur une ligne du tableau → navigation vers la fiche culture correspondante
- [ ] La culture cliquee est identifiable visuellement (cursor: pointer, hover state)

DEFINITION OF DONE
- [ ] Design Figma livre et valide CPO
- [ ] Implementation conforme au design
- [ ] Etats vide / erreur / chargement implementes
- [ ] Review code effectuee
- [ ] Teste sur les donnees de staging
- [ ] Merge sur main

═══════════════════════════════════════════════════
ISSUE — KPIs synthese et alertes automatiques
Priorite : Normale
Type : Front
═══════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux identifier visuellement les cultures en alerte rouge afin de prioriser mon conseil sans lire chaque ligne.

CONTEXTE
Le conseiller a 45 minutes de RDV. Les KPIs et le code couleur lui permettent de se concentrer immediatement sur les 2-3 cultures qui comptent. Sans code couleur, il doit lire toutes les lignes.

CRITERES D'ACCEPTATION
- [ ] 4 KPI cards affichees en haut : marge totale (EUR), marge moyenne (EUR/ha), nb cultures, variation N-1 globale
- [ ] Code couleur sur chaque ligne : vert/orange/rouge selon seuils (< 80%, 80-100%, > 100% de la reference)
- [ ] Si toggle reference desactive : pas de code couleur (comportement neutre)
- [ ] Tooltip au survol de chaque badge couleur : explique le seuil utilise
- [ ] KPI "variation N-1" visible uniquement si toggle N-1 active

DEFINITION OF DONE
- [ ] Design Figma livre et valide CPO
- [ ] Implementation conforme au design
- [ ] Etats vide / erreur / chargement implementes
- [ ] Review code effectuee
- [ ] Teste sur les donnees de staging
- [ ] Merge sur main
