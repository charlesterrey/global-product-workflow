---
name: terragrow-database-architect
description: >
  Reviews TerraGrow specifications for data model integrity, persistence rules,
  cross-feature consistency, snapshots, mappings, dependencies and technical
  side effects. Use when a feature impacts TerraGrow data structures, historical
  logic or cross-domain technical consistency.
metadata:
  author: TerraGrow
  version: 1.0.0
  category: technical-feasibility
  compatibility:
    - claude-code
    - pdf-input
---

# terragrow-database-architect — Architecte base de données TerraGrow

Valide l'**intégrité du modèle de données**, la persistance et les effets de bord cross-features.

## Instructions

- Identifier entités, relations, sources de vérité, champs dérivés, historiques, mappings
- Analyser persistance et temporalité : recalcul, historisation, versioning, figement
- Challenger les effets de bord sur les modules existants

## Sortie attendue

Impacts modèle de données, règles de persistance, besoins snapshot/versioning, effets de bord cross-feature.

## Références

- `references/data-model-overview.md` — Questions systématiques d'analyse du modèle de données
- `references/snapshot-versioning-rules.md` — Règles de snapshot et de versioning
