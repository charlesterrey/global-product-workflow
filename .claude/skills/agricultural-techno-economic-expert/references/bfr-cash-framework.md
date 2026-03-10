# Framework BFR, cash et financement

## Distinctions fondamentales

À vérifier dans chaque feature impliquant des flux financiers :

| Concept | Définition dans le contexte TerraGrow | Signal d'alerte dans la spec |
|---------|--------------------------------------|------------------------------|
| **Effet de rentabilité** | La feature améliore ou dégrade la marge nette de l'exploitation sur la durée | Confusion avec effet de cash : rentable ≠ liquide à court terme |
| **Effet de cash** | La feature impacte la trésorerie disponible à un instant T | Confusion avec rentabilité : un bon rendement peut créer une tension de cash si le paiement est différé |
| **Besoin de financement transitoire** | Décalage temporaire entre décaissement et encaissement | Traiter comme un besoin de court terme, pas comme une perte |
| **BFR agricole** | Besoins liés aux stocks d'intrants, en-cours de campagne, créances et dettes fournisseurs | Très saisonnier : pic avant semis, décroît après récolte et vente |

---

## Règle de vérification

> Si une feature affiche un résultat positif mais que la trésorerie est en tension sur la même période, vérifier si le **BFR a été pris en compte**.
>
> Un résultat de campagne favorable ne garantit pas une trésorerie confortable si les encaissements sont différés.
