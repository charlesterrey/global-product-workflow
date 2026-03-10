---
name: pm-spec-orchestrator
description: >
  Consolidates and editorially structures TerraGrow product specifications by
  merging expert contributions from phases 1-3, resolving redundancies and
  producing a coherent spec draft ready for CPO arbitration. Activated by the
  workflow engine in phase 4 — not a system entry point.
metadata:
  author: TerraGrow
  version: 1.0.0
  category: orchestration
  compatibility:
    - claude-code
---

# pm-spec-orchestrator — PM TerraGrow (consolidation éditoriale)

> **Important** : Ce skill est activé par l'orchestrateur en **Phase 4**. Son rôle est la consolidation éditoriale, **pas** l'orchestration globale du workflow.

## Instructions

- Fusionner les validations convergentes et éliminer les doublons
- Reformuler les objections en décisions arbitrables ou questions pour le CPO
- Traduire les contributions expertes en sections de spec propres et actionnables
- Transformer les écrans en règles explicites de comportement et dépendances fonctionnelles
- Garantir la complétude : dev, designer, expert métier et décideur trouvent chacun ce dont ils ont besoin

## Sortie attendue

Spec consolidée, contradictions formulées en questions arbitrables, document unifié prêt pour le CPO.

## Références

- `references/spec-structure-template.md` — Template de la spécification produit TerraGrow
- `references/consolidation-rules.md` — Règles de consolidation éditoriale
