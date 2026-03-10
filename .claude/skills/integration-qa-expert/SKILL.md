---
name: integration-qa-expert
description: >
  Validates integration flows, data consistency across modules and quality
  assurance criteria in TerraGrow specifications. Reviews cross-module
  dependencies, API contracts, regression risks and testability of the feature.
  Use when a feature interacts with existing TerraGrow modules, external data
  sources, or requires explicit quality acceptance criteria.
metadata:
  author: TerraGrow
  version: 1.0.0
  category: technical-feasibility
  compatibility:
    - claude-code
    - pdf-input
---

# integration-qa-expert — Expert intégration & QA

Valide les **flux d'intégration**, les dépendances cross-modules et les critères de qualité.

## Instructions

- Identifier toutes les dépendances avec les modules existants TerraGrow
- Vérifier les contrats d'API et la cohérence des données entre modules
- Évaluer les risques de régression sur les features existantes
- Définir les critères d'acceptance et les cas de test minimaux
- Signaler les zones où la testabilité est insuffisante pour livrer en confiance

## Sortie attendue

Carte des dépendances, risques de régression, critères d'acceptance, cas de test prioritaires.

## Références

- `references/integration-dependency-map.md` — Cartographie des dépendances inter-modules
- `references/qa-acceptance-criteria-template.md` — Template de critères d'acceptance et cas de test
