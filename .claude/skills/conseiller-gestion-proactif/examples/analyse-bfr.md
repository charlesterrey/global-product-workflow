# Exemple — Analyse BFR avec detection d'alerte

## Question

Analyse le BFR du GAEC des Tilleuls (grandes cultures, 220 ha, Beauce) sur 2024-2025 vs N-1.

## Donnees fournies

```json
{
  "exploitation": "GAEC des Tilleuls",
  "campagne": "2024-2025",
  "bilan": {
    "stocks": 185000, "creances_clients": 42000, "autres_creances": 15000,
    "dettes_fournisseurs": 95000, "dettes_fiscales_sociales": 38000, "autres_dettes_ct": 12000
  },
  "bilan_n_minus_1": {
    "stocks": 160000, "creances_clients": 38000, "autres_creances": 12000,
    "dettes_fournisseurs": 88000, "dettes_fiscales_sociales": 35000, "autres_dettes_ct": 10000
  }
}
```

## Reponse attendue

### Indicateurs cles

| Indicateur | 2024-2025 | 2023-2024 | Variation | Alerte |
|---|---|---|---|---|
| BFR total | 97 000 EUR | 77 000 EUR | +26% | ATTENTION |
| BFR en jours de CA | 48 j | 39 j | +9 j | ATTENTION |
| Stocks | 185 000 EUR | 160 000 EUR | +15,6% | ATTENTION |
| Creances | 57 000 EUR | 50 000 EUR | +14% | — |
| Dettes CT | 145 000 EUR | 133 000 EUR | +9% | — |

*CA estime a 740 000 EUR (SAU x rendement moyen Beauce) — hypothese a confirmer*

### Analyse

BFR +26% vs norme sectorielle +5 a +8%. Hausse tiree par les stocks (+25 000 EUR). Deux hypotheses : stockage volontaire (conjoncturel) ou derive approvisionnements (structurel).

### Recommandations

| # | Action | Impact | Effort | Priorite |
|---|---|---|---|---|
| 1 | Verifier nature des stocks | Diagnostic | Faible | Haute |
| 2 | Negocier delais fournisseurs +15j | ~18 000 EUR BFR libere | Moyen | Haute |
| 3 | Accelerer recouvrement creances | ~8 000 EUR BFR libere | Faible | Moyenne |

### Metadonnees
- Confiance : 0.75 (CA non fourni, estime)
- Donnees manquantes : compte de resultat, detail stocks, delais paiement
