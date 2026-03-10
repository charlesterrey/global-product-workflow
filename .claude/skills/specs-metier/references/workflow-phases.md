# Workflow Phases — TerraGrow Spec Engine

Description complète des 7 phases du workflow de spécification.

---

## Phase 0 — Cadrage initial

**Objectif :** Créer la structure initiale du document de travail central.

**Actions :**
1. Lire le brief PDF en intégralité et identifier :
   - Problème adressé
   - Intention produit
   - Hypothèses déjà posées
   - Enjeux business ou métier
   - Contraintes identifiées
2. Analyser chaque interface PNG : composants visibles, décisions de design déjà prises, états représentés, interactions implicites
3. Reformuler la promesse de la fonctionnalité en 2-3 phrases
4. Identifier le périmètre implicite de la feature
5. Lister les zones ambiguës et les questions ouvertes
6. Créer la structure initiale du document central avec les sections : Contexte, Promesse utilisateur, Périmètre, Composants UI, Questions ouvertes, Règles à définir

**Critère de fin :** Problème, promesse, périmètre et zones critiques clairement formulés.

---

## Phase 1 — Validation de la vérité métier

**Skills activés :** `agricultural-management-expert`, `agricultural-accounting-expert`, `agronomy-expert`, `agricultural-techno-economic-expert`

Chaque expert est activé séquentiellement avec l'instruction :
> « En tant que [nom du skill], analyse le document de travail actuel et le brief produit. Produis un diagnostic structuré à intégrer dans la section Vérité métier. »

**Critère de fin :** Logique métier défendable, hypothèses critiques explicites, frontières gestion/comptabilité clarifiées, valeur métier validée.

---

## Phase 2 — Validation valeur et compréhension utilisateur

**Skills activés :** `future-farm-advisor`, `conservative-farm-advisor`, `large-crop-farmer-persona`, `viticulture-farmer-persona`, `mixed-farming-livestock-persona`, `uiux-expert`

**Critère de fin :** Proposition de valeur compréhensible, feature crédible pour les utilisateurs visés, freins d'adoption identifiés, interfaces traduisibles en expérience utile.

---

## Phase 3 — Validation faisabilité et delivery

**Skills activés :** `terragrow-database-architect`, `terragrow-developer-reviewer`, `integration-qa-expert`, `product-analytics-expert`

**Critère de fin :** Feature implémentable sans ambiguïté majeure, dépendances visibles, règles structurantes explicites, éléments de suivi post-lancement définis.

---

## Phase 4 — Consolidation éditoriale

**Skill activé :** `pm-spec-orchestrator` (en mode consolidation, pas en mode orchestration)

**Critère de fin :** Spec cohérente, contradictions majeures arbitrables, limites et non-objectifs explicites.

---

## Phase 5 — Arbitrage produit

**Skill activé :** `cpo-scope-arbiter` — **Obligatoire sur toutes les specs.**

**Critère de fin :** Scope figé, must-have vs futur décidé, contradictions tranchées, spec décidable et livrable.

---

## Phase 6 — Validation stratégique (conditionnelle)

**Skill activé :** `ceo-strategic-validator` — Uniquement si :
- Impact sur différenciation produit
- Enjeux de monétisation
- Brique structurante de la vision
- Question de timing marché

**Critère de fin :** Feature validée stratégiquement, réorientée ou explicitement dépriorisée.
