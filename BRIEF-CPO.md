# Brief CPO — Template One-Pager

> Remplir ce template avant d'invoquer `/design-specs` ou `/specs-metier`.
> Temps de remplissage : 10-15 minutes.
> Un brief bien rempli = une spec generee du premier coup sans aller-retour.

---

## FEATURE

**Nom :** [Nom court de la feature ou de la page]

**Date :** [JJ/MM/AAAA]

**Version cible :** [v1.0 / v1.1 / v2.0]

---

## PROBLEME

**Situation actuelle :**
> Comment ca se passe aujourd'hui sans cette feature ? Soyez concret.
> Ex : "Le conseiller ouvre 8 fiches culture une par une pour comparer les marges. Ca prend 20 min. Il fait ca avant chaque RDV client."

**Impact mesure :**
> Quel est le cout de ce probleme ? (temps perdu, erreurs, frustration, perte de client)
> Ex : "20 min x 3 RDV/semaine x 50 conseillers = 5 000h/an perdues"

---

## SOLUTION

**Ce qu'on veut construire :**
> Decrivez la solution en 2-4 phrases. Pas besoin d'etre technique.
> Ex : "Une page qui affiche toutes les marges brutes de toutes les cultures d'un coup, avec comparaison N-1 et references sectorielles. Le conseiller voit en un coup d'oeil quelle culture pose probleme."

**Impact attendu :**
> Qu'est-ce que ca change concretement pour l'utilisateur ?
> Ex : "Preparation du RDV passe de 20 min a 5 min. Le conseiller peut prendre 40% de RDV en plus."

---

## UTILISATEURS

**Utilisateur principal :** [Conseiller de gestion / Expert-comptable / Agriculteur]

**Frequence d'usage :** [Quotidien / Hebdomadaire / Mensuel / Ponctuel]

**Utilisateur secondaire (si applicable) :** [Role] — [frequence]

**Contexte d'usage :**
> Quand exactement l'utilisateur utilise cette feature ? (avant un RDV, en clotureannuelle, pendant la campagne agricole, etc.)

---

## CE QU'ON PEUT FAIRE

> Listez les actions que l'utilisateur doit pouvoir faire sur cet ecran / avec cette feature.
> Format : verbe + objet. Max 8 elements.

- [ ] [Action 1 — ex : Comparer les marges brutes par culture sur une campagne]
- [ ] [Action 2]
- [ ] [Action 3]
- [ ] [Action 4]
- [ ] ...

---

## CE QU'ON NE FAIT PAS (dans cette version)

> Ce qui est hors scope pour cette version. Soyez explicite pour eviter les debordements.

- [Limitation 1 — et pourquoi : donnees pas disponibles / complexite / v2]
- [Limitation 2]
- ...

---

## DONNEES DISPONIBLES

**Ce qu'on a :**
> Quelles donnees sont deja dans la base / accessibles ?
> Ex : comptabilite analytique par culture, surfaces, rendements, prix de vente

**Ce qu'on n'a PAS encore :**
> Quelles donnees manquent ? Seront-elles disponibles ? Quand ?
> Ex : IFT par parcelle (prevu v2), references CER (API pas encore integree)

---

## INTERFACES FIGMA (pour /specs-metier uniquement)

**Lien Figma :** [URL du fichier Figma — acces view requis]

**Screens inclus :**
- [Screen 1 — nom]
- [Screen 2 — nom]
- ...

---

## QUESTIONS OUVERTES

> Ce que vous ne savez pas encore. Le skill posera des questions si besoin.

- [ ] [Question 1 — ex : Faut-il inclure les aides PAC dans le produit brut par culture ?]
- [ ] [Question 2]
- [ ] ...

---

## CONTRAINTES CONNUES

> Contraintes techniques, metier, reglementaires ou calendaires a respecter.

- [Contrainte 1 — ex : Doit fonctionner avec les donnees Isacompta et Cegid]
- [Contrainte 2 — ex : Livraison avant la periode de cloture (mars)]
- ...

---

## INSPIRATION

> References visuelles ou produits similaires dont vous vous inspirez (optionnel).

- [Lien ou nom du produit — ex : Dashboard Pennylane, Agreo, FarmForce]

---

*Ce template est concu pour le workflow global-product-workflow TerraGrow.*
*Invoquer `/design-specs [coller ce brief]` pour la spec designer.*
*Invoquer `/specs-metier [coller ce brief + lien Figma]` pour la spec dev.*
