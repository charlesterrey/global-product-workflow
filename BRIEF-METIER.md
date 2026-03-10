# Brief Metier — Template CPO
> Utiliser avant d'invoquer `/specs-metier`
> Prerequis : le design est valide, les Figma sont prets.
> Temps : 15 minutes. L'objectif est de donner aux 17 experts tout ce qu'ils ont besoin pour ne pas inventer.

---

## FEATURE

**Nom :** [Meme nom que le brief design]
**Date :** [JJ/MM/AAAA]
**Version cible :** [v1.0 / v1.1 / v2.0]
**Brief design de reference :** [Lien ou date du brief design associe]

---

## INTERFACES FIGMA

**Lien Figma :** [URL — acces view requis pour Claude]

**Screens inclus :**
- [Screen 1 — ex : Vue principale dashboard]
- [Screen 2 — ex : Etat vide]
- [Screen 3 — ex : Etat erreur CER]
- [Screen 4 — ex : Toggle N-1 active]

**Ce qui a change par rapport au brief design initial :**
> Le designer a-t-il fait des choix qui modifient le scope ou les regles ?
> Ex : "Le designer a ajoute un filtre par type de sol — c'etait pas prevu, est-ce qu'on le garde ?"

---

## UTILISATEUR & IMPACT

**Utilisateur principal :** [Role] — [frequence]
**Impact metier attendu :** [Ce qui doit changer concretement — mesurable]

---

## REGLES METIER CONNUES

> Ce que vous savez deja sur la logique metier. Les experts valideront et completeront.

**Formules et calculs :**
> Ex : Marge brute = Produit brut - Charges operationnelles. Produit brut inclut les aides PAC couplees.

**Seuils et alertes :**
> Ex : Alerte rouge si marge < 80% de la reference CER, orange si 80-100%

**Regles specifiques au domaine agricole :**
> Ex : Aides PAC decouplees exclues du calcul par culture, imputees au niveau exploitation

---

## PERIMETRE TECHNIQUE

**Ce qu'on implémente dans cette version :**
- [Fonctionnalite 1]
- [Fonctionnalite 2]

**Hors scope (confirme) :**
- [Ex : Export Excel — v2]
- [Ex : IFT par parcelle — donnees manquantes]

---

## DONNEES & INTEGRATIONS

**Donnees disponibles dans TerraGrow :**
> Ex : accounting_entries par culture, Exploitation.region_id, Campagne.statut

**Donnees manquantes ou a creer :**
> Ex : Pas de cache pour les references CER — a creer

**Sources externes :**
> Ex : API CER pour les references regionales — endpoint a confirmer avec l'equipe CER

**Modules TerraGrow concernes :**
> Ex : Module Comptabilite analytique, Module Exploitations, Module Campagnes

---

## CONTRAINTES TECHNIQUES

> Performances, compatibilite, infrastructure, securite.

- [Ex : Temps de reponse API < 500ms pour 20 cultures]
- [Ex : Doit fonctionner avec Isacompta et Cegid]
- [Ex : Livraison avant la periode de cloture (mars)]

---

## QUESTIONS OUVERTES

> Ce que vous ne savez pas encore et que les experts devront trancher.

- [ ] [Ex : Faut-il versionner les references CER ou toujours afficher la derniere ?]
- [ ] [Ex : Que faire si l'API CER retourne une reference negative ?]
- [ ]

---

## DECISIONS DEJA PRISES (ne pas remettre en question)

> Ce qui est arrete et ne doit pas etre rediscute par les experts.

- [Ex : Le code couleur utilise les seuils 80% / 100% — decision CPO]
- [Ex : Les aides decouplees sont exclues — decision Expert-Comptable validee]

---

*Invoquer `/specs-metier [coller ce brief]` dans Claude Code.*
*Le skill orchestrera automatiquement les 17 experts et generera la spec + les issues.*
