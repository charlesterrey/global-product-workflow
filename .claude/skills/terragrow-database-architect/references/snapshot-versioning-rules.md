# Règles de snapshot et de versioning

## Critères déclenchant un besoin de snapshot ou de versioning

- Données affichées dans un **rapport ou un bilan envoyé à l'agriculteur** → snapshot obligatoire
- Données utilisées dans une **comparaison prévisionnelle vs réalisée** → snapshot du prévisionnel au moment de la validation
- Données pouvant être **recalculées rétroactivement** → vérifier si la rétroactivité est souhaitée ou dangereuse
- Données liées à une **clôture d'exercice ou de campagne** → figer à la date de clôture
- Données consultées par **plusieurs utilisateurs avec des droits différents** → versionner selon le rôle

---

## Règle générale

> Ce qui a été **vu, validé ou partagé** ne doit pas changer silencieusement.
>
> Un recalcul rétroactif doit être **explicitement documenté** dans la spec et **traçable** dans l'interface.
