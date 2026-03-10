# Exemple — Analyse d'un itineraire ble tendre

## Question

Analyse l'itineraire cultural du ble tendre sur la parcelle "Les Grands Champs" (GAEC des Tilleuls, Beauce, limon profond, precedent colza).

## Donnees fournies

```json
{
  "culture": "ble tendre", "parcelle": "Les Grands Champs",
  "surface_ha": 35, "sol": "limon profond", "region": "Beauce",
  "precedent": "colza", "campagne": "2024-2025",
  "variete": "Chevignon", "date_semis": "2024-10-15",
  "densite_semis_grains_m2": 280,
  "itineraire": [
    {"operation": "dechaumage", "date": "2024-08-20", "outil": "cover crop"},
    {"operation": "dechaumage", "date": "2024-09-05", "outil": "cover crop"},
    {"operation": "dechaumage", "date": "2024-09-25", "outil": "cultivateur"},
    {"operation": "labour", "date": "2024-10-08", "profondeur_cm": 25},
    {"operation": "semis combine", "date": "2024-10-15"},
    {"operation": "herbicide", "date": "2024-11-10", "produit": "chlortoluron + DFF", "dose_l_ha": 2.5},
    {"operation": "apport N1", "date": "2025-02-15", "forme": "ammonitrate 33.5%", "dose_kg_ha": 100},
    {"operation": "apport N2", "date": "2025-03-20", "forme": "solution azotee 39", "dose_l_ha": 200},
    {"operation": "apport N3", "date": "2025-04-15", "forme": "ammonitrate 33.5%", "dose_kg_ha": 150},
    {"operation": "fongicide T1", "date": "2025-04-10", "produit": "prothioconazole", "dose_l_ha": 0.8},
    {"operation": "fongicide T2", "date": "2025-05-05", "produit": "bixafen + prothioconazole", "dose_l_ha": 1.0},
    {"operation": "fongicide T3", "date": "2025-05-25", "produit": "metconazole", "dose_l_ha": 0.8},
    {"operation": "recolte", "date": "2025-07-18", "rendement_q_ha": 85}
  ]
}
```

## Reponse attendue

### Analyse du systeme de culture

Ble tendre Chevignon — 35 ha — Limon profond — Beauce
Precedent colza (bon precedent azote : ~20-30 u N de credit)
Rendement realise : 85 q/ha

### Incoherences detectees

| # | Incoherence | Gravite | Explication |
|---|---|---|---|
| 1 | 3 dechaumages apres colza | Moderee | 1 passage excedentaire (~25 EUR/ha inutile) |
| 2 | Densite semis 280 gr/m2 | Faible | Surdensite ~30-50 gr/m2 (~8-12 EUR/ha surcout) |
| 3 | T3 fongicide systematique | Moderee | Rentabilite non garantie sans pression fusariose (~35 EUR/ha) |

### Recommandations

| # | Recommandation | Impact rendement | Impact cout | Priorite |
|---|---|---|---|---|
| 1 | Supprimer 1 dechaumage apres colza | Nul | -25 EUR/ha | Haute |
| 2 | Reduire densite semis a 240 gr/m2 | Nul | -10 EUR/ha | Moyenne |
| 3 | Conditionner T3 a l'observation epi | -2 q/ha si pression reelle | -35 EUR/ha si supprime | Haute |

### Impacts technico-economiques

| Cumul | Rendement | Charges/ha | Marge/ha |
|---|---|---|---|
| Total | -1 q/ha | -52,5 EUR | +40 EUR net |

Potentiel d'economie sur 35 ha : ~1 400 EUR/an sans degradation significative du rendement.

### Metadonnees
- Confiance : 0.85
- Sources : ARVALIS (densites Beauce), COMIFER (fertilisation), Ecophyto Centre-Val de Loire (IFT)
- Donnees manquantes : analyse sol, reliquat azote sortie hiver, historique pression sanitaire
