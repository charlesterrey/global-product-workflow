# Brief Design — Template CPO
> Utiliser avant d'invoquer `/design-specs`
> Temps : 10 minutes. Le designer n'a pas encore travaille.
> Objectif : lui donner assez de contexte pour fermer les yeux et imaginer l'ecran.

---

## FEATURE

**Nom :** [Nom court — ex : Dashboard Marges par Culture]
**Date :** [JJ/MM/AAAA]
**Version cible :** [v1.0 / v1.1 / v2.0]

---

## PROBLEME A RESOUDRE

**Aujourd'hui, l'utilisateur fait comment ?**
> Decrivez le workflow actuel — concret, sans TerraGrow. Citez le temps perdu, les outils, les frustrations.
> Ex : "Le conseiller ouvre 8 fiches culture une par une. Ca prend 20 min avant chaque RDV."

**Quel est l'impact de ce probleme ?**
> Ex : "3 RDV/semaine x 20 min x 50 conseillers = 5 000h/an perdues. Certains ne preparent plus."

---

## CE QU'ON VEUT CONSTRUIRE

**La solution en 2-4 phrases :**
> Ne soyez pas technique. Decrivez ce que l'utilisateur va pouvoir faire.
> Ex : "Une page qui montre toutes les marges de toutes les cultures d'un coup. Le conseiller voit en 2 min quelle culture pose probleme."

**Ce que ca change pour l'utilisateur :**
> Ex : "Preparation RDV : 20 min → 5 min. Le conseiller conseille au lieu de chercher des chiffres."

---

## UTILISATEUR

**Qui utilise cet ecran ?** [Conseiller de gestion / Expert-comptable / Agriculteur]

**A quelle frequence ?** [Quotidien / Hebdomadaire / Mensuel / Avant chaque RDV / En cloture]

**Dans quel contexte ?**
> Quand exactement dans sa journee / semaine ? Quel est son etat d'esprit ?
> Ex : "La veille d'un RDV, il a 10 min pour preparer. Il est sur son laptop au bureau."

---

## CE QU'ON PEUT FAIRE

> Actions que l'utilisateur doit pouvoir faire sur cet ecran. Verbe + objet. Max 8.

- [ ] [Ex : Voir les marges brutes de toutes les cultures sur une campagne]
- [ ] [Ex : Comparer avec la campagne precedente]
- [ ] [Ex : Identifier les cultures en alerte]
- [ ]
- [ ]

---

## CE QU'ON NE FAIT PAS

> Hors scope pour cette version. Etre explicite evite les debordements.

- [Ex : Export Excel — prevu v2]
- [Ex : Simulation de prix — trop complexe, v2]
- [Ex : Comparaison multi-exploitations — feature differente]

---

## DONNEES DISPONIBLES

**Ce qu'on a dans TerraGrow :**
> Ex : Comptabilite analytique par culture, surfaces, rendements, prix de vente

**Ce qu'on n'a PAS encore :**
> Ex : IFT par parcelle (prevu v2), references CER (API pas encore integree)

---

## QUESTIONS OUVERTES

> Ce que vous ne savez pas encore. Le skill demandera si besoin.

- [ ] [Ex : Les aides PAC sont-elles incluses dans le produit brut par culture ?]
- [ ]

---

## INSPIRATION (optionnel)

> References visuelles ou produits dont vous vous inspirez.
> Ex : Dashboard Pennylane, Agreo, FarmForce

---

*Invoquer `/design-specs [coller ce brief]` dans Claude Code.*
