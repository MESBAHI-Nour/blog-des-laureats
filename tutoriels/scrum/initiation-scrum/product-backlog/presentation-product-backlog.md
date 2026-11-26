---
marp: true
theme: default
size: 16:9
paginate: true
---

<!-- _class: lead -->
![Logo OFPPT](../../../images/ofppt-logo.png) ![Logo SoliCode](../../../images/solicode-logo.png)
# Créer, estimer et ordonner le Product Backlog

### Projet technique : Streamix — Plateforme de streaming / Films
**Présenté par** : Mesbahi Nour
**Encadré par** : ES-Sarraj Fouad

---

# Plan

1. Product Backlog
2. Story Points et Fibonacci
3. Priorisation MoSCoW
4. Exemple Streamix et MVP
5. DoR et DoD

---

# 1. Product Backlog

- Liste ordonnée des besoins du produit
- Évolue pendant le projet
- Géré par le Product Owner
- Priorisé selon la valeur métier

---

# 2. Story Points

- Mesurent l'effort relatif
- Comparaison entre User Stories
- Considèrent complexité et incertitude
- Ne représentent pas des heures

---

# Suite de Fibonacci

| Points | Effort relatif |
|---:|---|
| 1 | Très simple |
| 2 | Simple |
| 3 | Moyen |
| 5 | Complexe |
| 8 | Très complexe |

**Échelle utilisée : 1 · 2 · 3 · 5 · 8**

---

# 3. Priorisation MoSCoW

- **Must** : indispensable
- **Should** : important
- **Could** : facultatif
- **Won't** : pas dans cette version

**MVP : première version utile et minimale**

---

# 4. Product Backlog — Streamix

| ID | User Story | SP | Priorité |
|---|---|---:|---|
| US01 | Consulter le catalogue | 3 | Must |
| US02 | Voir la fiche d'un film | 2 | Must |
| US03 | Ajouter un film | 5 | Must |
| US04 | Modifier un film | 3 | Should |
| US05 | Supprimer un film | 2 | Should |

---

# Product Backlog — Suite

| ID | User Story | SP | Priorité |
|---|---|---:|---|
| US06 | Filtrer par genre | 3 | Should |
| US07 | Voir les films d'un réalisateur | 2 | Could |
| US08 | Recommandations personnalisées | 8 | Won't |

**Les priorités peuvent évoluer avec les besoins.**

---

# MVP proposé — Sprint 1

- US01 : consulter le catalogue — 3 SP
- US02 : voir une fiche — 2 SP
- US03 : ajouter un film — 5 SP

# Total : 10 Story Points

<small>Capacité du Sprint à confirmer avec l'équipe.</small>

---

# 5. Definition of Ready — DoR

### Avant de commencer

- Story claire et compréhensible
- Valeur métier connue
- Critères d'acceptation définis
- Dépendances identifiées
- Estimation validée par l'équipe

---

# Definition of Done — DoD

### Pour terminer une story

- Développement terminé
- Critères d'acceptation respectés
- Contrôles fonctionnels réussis
- Données correctement traitées
- Aucun défaut bloquant connu
- Code relu et intégré

---

# DoR ≠ DoD

| DoR | DoD |
|---|---|
| Avant le Sprint | Pendant et à la fin du travail |
| Story prête | Story terminée |
| Peut-on commencer ? | Est-ce vraiment fini ? |

---

<!-- _class: lead -->

# Conclusion

**Backlog organisé · Effort estimé · Priorités claires · Qualité vérifiée**

Streamix avance fonctionnalité par fonctionnalité.
