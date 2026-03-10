# Exemple — Spec Metier : Dashboard Marges par Culture

## Input

> Brief CPO + interfaces Figma validees par le designer
> Experts actives : agricultural-management-expert, agricultural-accounting-expert, agronomy-expert, uiux-expert, terragrow-database-architect, terragrow-developer-reviewer, integration-qa-expert, product-analytics-expert, pm-spec-orchestrator, cpo-scope-arbiter

---

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DOCUMENT 1 — SPEC METIER
Dashboard Marges par Culture — v2025-03
Experts consultes : agricultural-management-expert, agricultural-accounting-expert, agronomy-expert, uiux-expert, terragrow-database-architect, terragrow-developer-reviewer, integration-qa-expert, product-analytics-expert
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 1. Contexte & Vision

**Probleme adresse :** Le conseiller de gestion navigue entre 5 a 8 fiches culture individuelles pour aggreger les marges brutes avant chaque RDV. Aucune vue synthetique n'existe. Temps moyen : 15-20 minutes par exploitation.

**Solution TerraGrow :** Un dashboard de comparaison des marges brutes par culture, avec toggle N-1 et references sectorielles CER. Reduction de la preparation RDV de 20 min a 5 min.

**Utilisateur principal :** Conseiller de gestion — hebdomadaire (avant RDV client)

**Impact metier :** +40% de capacite de RDV par conseiller. Detection immediate des cultures sous-performantes. Conseil base sur des donnees plutot que sur la memoire.

**Lien Figma :** [URL des interfaces validees]

---

## 2. User Stories

**US-1** | En tant que conseiller de gestion, je veux voir les marges brutes de toutes les cultures sur une seule page afin de preparer mon RDV en 5 minutes.
> Contexte metier : Campagne agricole standard avec 3 a 12 cultures par exploitation. Le conseiller consulte cette page la veille ou le matin du RDV.
> Priorite : Must-have

**US-2** | En tant que conseiller de gestion, je veux comparer les marges avec N-1 afin de detecter les derives et expliquer les ecarts a l'agriculteur.
> Contexte metier : L'ecart N/N-1 est l'indicateur de conseil le plus utilise en gestion agricole. Il permet de distinguer un probleme conjoncturel (prix marche) d'un probleme structurel (charges trop elevees).
> Priorite : Must-have

**US-3** | En tant que conseiller de gestion, je veux comparer avec les references CER afin de situer la performance par rapport au marche.
> Contexte metier : Les references CER (Centres d'Economie Rurale) sont le benchmark standard en France. Elles sont disponibles par region, par culture et par campagne.
> Priorite : Must-have

**US-4** | En tant que conseiller de gestion, je veux identifier visuellement les cultures en alerte afin de prioriser mon conseil sans analyser chaque ligne.
> Contexte metier : Seuils metier valides par agricultural-management-expert : alerte critique si marge < 80% de la reference, attention si 80-100%, nominal si > 100%.
> Priorite : Must-have

**US-5** | En tant que conseiller de gestion, je veux acceder a la fiche detail d'une culture depuis le dashboard afin de comprendre les postes de charges responsables d'une derive.
> Contexte metier : La fiche culture existante contient le detail des charges operationnelles, de mecanisation et des aides PAC. La navigation doit etre directe, sans retour a la liste.
> Priorite : Should-have

---

## 3. Regles metier

**FORMULES & CALCULS**

| Indicateur | Formule | Unite | Source |
|---|---|---|---|
| Marge brute/ha | (Produit brut - Charges operationnelles) / Surface | EUR/ha | agricultural-accounting-expert |
| Produit brut/ha | (Ventes + Variation stocks + Aides PAC couplees) / Surface | EUR/ha | agricultural-accounting-expert |
| Charges operationnelles/ha | (Semences + Engrais + Phytos + Autres intrants) / Surface | EUR/ha | agricultural-accounting-expert |
| Marge brute totale | Somme des marges brutes totales de toutes les cultures | EUR | agricultural-accounting-expert |
| Ecart vs N-1 | (Marge brute N - Marge brute N-1) / Marge brute N-1 | % | agricultural-management-expert |
| Ecart vs reference | (Marge brute exploitation - Reference CER) / Reference CER | % | agricultural-management-expert |

**REGLES DE GESTION**

- Aides PAC couplees : incluses dans le produit brut par culture. Aides decoupleess : exclues (imputees au niveau exploitation, pas par culture). Source : agricultural-accounting-expert.
- Une culture sans donnees comptables completes est affichee avec mention "(incomplet)" — elle n'est pas exclue du calcul.
- La marge brute minimale affichable est -9 999 EUR/ha. Au-dela, afficher "> -9999" pour eviter les distorsions graphiques.
- La campagne selectionnee par defaut est la derniere campagne cloturee. Si aucune campagne cloturee : campagne en cours.

**SEUILS & ALERTES** (valides par agricultural-management-expert)

- Alerte CRITIQUE (rouge) : marge brute < 80% de la reference CER
- Alerte ATTENTION (orange) : marge brute entre 80% et 100% de la reference
- Nominal (vert) : marge brute > 100% de la reference
- Si references CER desactivees : aucun code couleur, affichage neutre

**CONTRAINTES METIER**

- Les references CER sont regionales. La region est liee au siege de l'exploitation (champ existant).
- Si la reference CER n'existe pas pour une culture donnee dans la region : afficher "—" en colonne reference, pas d'alerte couleur.
- Les donnees de N-1 peuvent etre incompletes si la campagne precedente n'a pas ete saisie. Gerer ce cas sans bloquer l'affichage N.

---

## 4. Ce qu'on fait / Ce qu'on NE FAIT PAS

✅ PERIMETRE DE CETTE VERSION
- Affichage des marges brutes par culture pour une campagne donnee
- Toggle comparaison N-1 (colonne + graphique groupes)
- Toggle references CER regionales
- Code couleur automatique selon seuils 80%/100%
- KPIs synthese (marge totale, marge moyenne, nb cultures, variation N-1)
- Tri du tableau par toutes les colonnes
- Navigation vers la fiche culture existante

🚫 HORS PERIMETRE (et pourquoi)
- Export Excel / PDF — prevu v2 ; donnees disponibles mais fonctionnalite non prioritaire
- Simulation de prix ou de rendement — complexite metier elevee ; necessite un moteur de calcul dedie, v2
- IFT (Indice de Frequence de Traitement) par parcelle — donnees non disponibles dans TerraGrow aujourd'hui
- Comparaison multi-exploitations — perimetre feature "portefeuille conseiller", scope different
- Charges de mecanisation ventilees par culture dans ce dashboard — disponible dans la fiche detail culture

⚠️ HYPOTHESES CRITIQUES
- Les donnees comptables analytiques par culture sont saisies et disponibles pour la campagne selectionnee
- L'API CER fournit des references par region, culture et campagne avec un taux de disponibilite > 95%
- La region de l'exploitation est correctement renseignee dans TerraGrow

---

## 5. Modele de donnees

**ENTITES IMPACTEES**

| Entite | Action | Champs concernes | Notes |
|---|---|---|---|
| CultureRecord | READ | marge_brute_ha, surface_ha, rendement_qha, campagne_id | Agregation depuis accounting_entries |
| Campagne | READ | id, annee, statut (en_cours / cloturee) | Filtre sur statut pour dropdown |
| Exploitation | READ | id, nom, region_id | Region pour filtrage references CER |
| CERReference | READ (API externe) | culture_type, region_id, campagne_annee, reference_marge_ha | Cache 24h recommande |

**NOUVELLE ENTITE — CERReferenceCache**
```
CERReferenceCache {
  id            : UUID
  culture_type  : string       — type de culture (ble_tendre, colza, etc.)
  region_id     : UUID         — reference Region
  campagne_annee: integer      — annee de la campagne
  reference_marge_ha : decimal — valeur de reference EUR/ha
  fetched_at    : timestamp    — date de recuperation
  expires_at    : timestamp    — TTL 24h
}
```

**DONNEES HISTORIQUES**
- Les marges brutes sont calculees a la volee depuis les accounting_entries. Pas de snapshotting necessaire pour v1.
- Le cache CER est purgeable manuellement par un admin si les references sont mises a jour en cours de campagne.

---

## 6. Contrats & Integrations

**ENDPOINTS API**

| Methode | Route | Payload | Reponse |
|---|---|---|---|
| GET | /api/v1/exploitations/:id/marges-cultures | campagne_id, include_n1 (bool), include_cer (bool) | { cultures: CultureMarge[], kpis: KPISynthese } |
| GET | /api/v1/cer-references | region_id, campagne_annee, culture_types[] | { references: CERReference[] } |

**Format CultureMarge :**
```json
{
  "culture_id": "uuid",
  "culture_nom": "Ble tendre",
  "surface_ha": 45.5,
  "rendement_qha": 72.3,
  "marge_brute_ha": 285.0,
  "marge_brute_totale": 12967.5,
  "n1_marge_brute_ha": 310.0,
  "ecart_n1_pct": -8.1,
  "cer_reference_ha": 320.0,
  "ecart_cer_pct": -10.9,
  "alerte_niveau": "attention",
  "donnees_completes": true
}
```

**DEPENDANCES INTER-MODULES**
- Module Comptabilite analytique → fournit les accounting_entries par culture
- Module Exploitations → fournit region_id pour filtrage CER
- Module Campagnes → fournit la liste des campagnes disponibles

**SOURCES DE DONNEES EXTERNES**
- API CER : references sectorielles — consommation au premier acces + cache 24h. Endpoint : a confirmer avec l'equipe CER.

**EVENTS ANALYTICS**

| Evenement | Declencheur | Proprietes |
|---|---|---|
| marges_dashboard_viewed | Ouverture de la page | exploitation_id, campagne_id, nb_cultures |
| marges_toggle_n1_activated | Clic toggle N-1 vers ON | exploitation_id, campagne_id |
| marges_toggle_cer_activated | Clic toggle CER vers ON | exploitation_id, campagne_id |
| marges_culture_drilldown | Clic sur une ligne culture | exploitation_id, culture_id, alerte_niveau |
| marges_campagne_changed | Changement de campagne | exploitation_id, from_campagne, to_campagne |


━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DOCUMENT 2 — ISSUES LINEAR
Dashboard Marges par Culture — 5 issues
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

═══════════════════════════════════════════════════════
ISSUE — API : endpoint marges brutes par culture
Priorite : Critique
Type : Back
Effort estime : L
═══════════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux voir les marges brutes de toutes les cultures sur une seule page afin de preparer mon RDV en 5 minutes.

CONTEXTE METIER
La marge brute = (Produit brut - Charges operationnelles) / Surface. Le produit brut inclut les aides PAC couplees mais PAS les aides decouplees. Cette distinction est critique pour la validite metier. Source : agricultural-accounting-expert.

REGLES METIER APPLICABLES
- Marge brute/ha = (Produit brut - Charges ope) / Surface
- Produit brut inclut aides PAC couplees, exclut aides decouplees
- Culture sans donnees completes : retourner avec donnees_completes=false, ne pas exclure

CRITERES D'ACCEPTATION
- [ ] GET /api/v1/exploitations/:id/marges-cultures retourne toutes les cultures de la campagne
- [ ] Chaque culture contient : surface_ha, rendement_qha, marge_brute_ha, marge_brute_totale
- [ ] Parametre include_n1=true retourne les donnees N-1 si disponibles
- [ ] Parametre include_cer=true declenche la recuperation des references CER (cache 24h)
- [ ] Culture avec donnees manquantes retourne donnees_completes=false (pas d'erreur 404)
- [ ] Temps de reponse < 500ms pour une exploitation avec 20 cultures
- [ ] Aucune aides decouplees incluse dans le produit brut

DEFINITION OF DONE
- [ ] Code implementé et review effectuee
- [ ] Tests unitaires ecrits (couverture > 80%)
- [ ] Tests d'integration passes
- [ ] Etats vide / erreur / chargement geres
- [ ] Conforme au design Figma valide
- [ ] Documente dans le changelog interne
- [ ] Deploye en staging et valide CPO
- [ ] Merge sur main

═══════════════════════════════════════════════════════
ISSUE — Cache references CER + entite CERReferenceCache
Priorite : Haute
Type : Back
Effort estime : M
═══════════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux comparer avec les references CER afin de situer la performance par rapport au marche.

CONTEXTE METIER
Les references CER sont regionales. Si l'API CER est indisponible, le dashboard doit continuer a fonctionner normalement (mode degradé gracieux). Le cache de 24h evite de sur-solliciter l'API externe.

REGLES METIER APPLICABLES
- References filtrees par : region_id de l'exploitation + culture_type + campagne_annee
- Si reference absente pour une culture : retourner null (pas d'alerte couleur cote frontend)
- Seuils alertes : critique < 80% reference, attention 80-100%, nominal > 100%

CRITERES D'ACCEPTATION
- [ ] Creation de l'entite CERReferenceCache avec TTL 24h
- [ ] Premier appel : fetch API CER + mise en cache
- [ ] Appels suivants : lecture depuis cache si non expire
- [ ] Si API CER indisponible : retourner donnees du cache si disponible, sinon null (pas d'erreur 500)
- [ ] Endpoint GET /api/v1/cer-references accepte region_id, campagne_annee, culture_types[]
- [ ] Purge manuelle possible par un admin (endpoint admin ou rake task)

DEFINITION OF DONE
- [ ] Code implementé et review effectuee
- [ ] Tests unitaires ecrits (couverture > 80%)
- [ ] Tests d'integration passes
- [ ] Etats vide / erreur / chargement geres
- [ ] Conforme au design Figma valide
- [ ] Documente dans le changelog interne
- [ ] Deploye en staging et valide CPO
- [ ] Merge sur main

═══════════════════════════════════════════════════════
ISSUE — Frontend : dashboard marges avec graphique et tableau
Priorite : Critique
Type : Front
Effort estime : L
═══════════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux voir les marges brutes de toutes les cultures sur une seule page afin de preparer mon RDV en 5 minutes.

CONTEXTE METIER
L'interface doit permettre une lecture instantanee. Le graphique a barres horizontales (culture en Y, marge EUR/ha en X) est plus lisible qu'un graphique vertical pour des noms de cultures longs.

REGLES METIER APPLICABLES
- Tri par defaut : marge brute/ha decroissant (cultures les plus rentables en haut)
- Donnees incompletes : afficher "(incomplet)" avec tooltip explicatif
- Marge negative : affichable, pas de traitement special

CRITERES D'ACCEPTATION
- [ ] Affichage des 4 KPIs synthese en haut de page
- [ ] Graphique bar chart horizontal : culture en Y, marge EUR/ha en X
- [ ] Tableau avec colonnes : Culture | Surface | Rendement | Marge/ha | Marge totale
- [ ] Tri cliquable sur toutes les colonnes, fleche indicatrice de direction
- [ ] Skeleton loader pendant le chargement
- [ ] Etat vide : message + CTA "Ajouter une culture"
- [ ] Dropdown campagne fonctionnel (toutes campagnes disponibles)

DEFINITION OF DONE
- [ ] Code implementé et review effectuee
- [ ] Tests unitaires ecrits (couverture > 80%)
- [ ] Tests d'integration passes
- [ ] Etats vide / erreur / chargement geres
- [ ] Conforme au design Figma valide
- [ ] Documente dans le changelog interne
- [ ] Deploye en staging et valide CPO
- [ ] Merge sur main

═══════════════════════════════════════════════════════
ISSUE — Frontend : toggles N-1 et CER + code couleur alertes
Priorite : Haute
Type : Front
Effort estime : M
═══════════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux activer la comparaison N-1 et les references CER afin d'enrichir l'analyse selon mes besoins du moment.

CONTEXTE METIER
Les deux toggles sont independants. Un conseiller peut activer N-1 sans activer CER et inversement. Le code couleur ne s'affiche QUE si le toggle CER est actif — sinon affichage neutre.

REGLES METIER APPLICABLES
- Toggle N-1 ON : afficher colonne Var N-1 (%) + barres groupees sur graphique
- Toggle CER ON : afficher colonne vs Ref (%) + ligne reference sur graphique + code couleur
- Code couleur : rouge < 80% ref, orange 80-100%, vert > 100%
- Si CER OFF : aucun code couleur, meme si N-1 actif

CRITERES D'ACCEPTATION
- [ ] Toggle N-1 : desactive par defaut, active/desactive la colonne et les barres groupees
- [ ] Toggle CER : desactive par defaut, active/desactive la colonne et la ligne reference
- [ ] Code couleur applique uniquement si toggle CER actif
- [ ] Tooltip sur badge couleur : explique le seuil (ex : "Marge < 80% de la reference CER")
- [ ] Si reference CER indisponible pour une culture : afficher "—" sans badge couleur
- [ ] Etat des toggles conserve lors d'un changement de campagne dans la meme session

DEFINITION OF DONE
- [ ] Code implementé et review effectuee
- [ ] Tests unitaires ecrits (couverture > 80%)
- [ ] Tests d'integration passes
- [ ] Etats vide / erreur / chargement geres
- [ ] Conforme au design Figma valide
- [ ] Documente dans le changelog interne
- [ ] Deploye en staging et valide CPO
- [ ] Merge sur main

═══════════════════════════════════════════════════════
ISSUE — Navigation vers fiche culture + tracking analytics
Priorite : Normale
Type : Front
Effort estime : S
═══════════════════════════════════════════════════════

USER STORY
En tant que conseiller de gestion, je veux cliquer sur une culture pour acceder au detail afin de comprendre les charges qui expliquent une derive.

CONTEXTE METIER
La fiche culture existante contient le detail des charges. La navigation doit etre directe (pas de modal intermediaire). Les events analytics permettront de mesurer l'adoption du dashboard et d'identifier les patterns de conseil.

REGLES METIER APPLICABLES
- Clic sur ligne tableau → navigation vers /cultures/:id (fiche existante)
- Events a tracker : dashboard_viewed, toggle_n1_activated, toggle_cer_activated, culture_drilldown, campagne_changed

CRITERES D'ACCEPTATION
- [ ] Clic sur ligne tableau → navigation vers fiche culture
- [ ] Cursor pointer + hover state sur les lignes cliquables
- [ ] Event culture_drilldown fire avec exploitation_id, culture_id, alerte_niveau
- [ ] Event marges_dashboard_viewed fire a l'ouverture avec nb_cultures, campagne_id
- [ ] Events toggles fires au moment de l'activation (pas de la desactivation)

DEFINITION OF DONE
- [ ] Code implementé et review effectuee
- [ ] Tests unitaires ecrits (couverture > 80%)
- [ ] Tests d'integration passes
- [ ] Etats vide / erreur / chargement geres
- [ ] Conforme au design Figma valide
- [ ] Documente dans le changelog interne
- [ ] Deploye en staging et valide CPO
- [ ] Merge sur main
