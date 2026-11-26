---
marp: true
theme: default
size: 16:9
paginate: true
style: |
  section {
    font-family: Arial, sans-serif;
    background: #ffffff;
    color: #1f2937;
    padding: 48px;
  }
  h1, h2 {
    color: #1d4ed8;
  }
  h1 {
    font-size: 2.1em;
  }
  h2 {
    font-size: 1.55em;
  }
  p, li {
    font-size: 0.92em;
  }
  section.lead {
    background: #0f172a;
    color: #ffffff;
    text-align: center;
  }
  section.lead h1, section.lead h2 {
    color: #ffffff;
  }
---

<!-- _class: lead -->
![Logo OFPPT](../../../images/ofppt-logo.png) ![Logo SoliCode](../../../images/solicode-logo.png)

# Vision Produit & User Stories

**Présenté par** : Mesbahi Nour
**Encadré par** : ES-Sarraj Fouad

---

# Plan

1. Vision Produit
2. Personas cibles
3. User Stories
4. Critères d'acceptation
5. MVP et évolutions

---

# 1. Présentation de Streamix

- Plateforme de découverte de films
- Catalogue classé par genre et réalisateur
- Gestion du catalogue par l'administrateur

**Données principales :** Réalisateur · Film · Genre

---

# 2. Vision Produit

> Découvrir et retrouver facilement des films grâce à un catalogue simple, organisé et consultable.

**Valeur :**

- Visiteur : trouver et découvrir
- Administrateur : organiser et actualiser

---

# 3. Personas cibles

| Amine — Visiteur | Sara — Administratrice |
|---|---|
| 22 ans, étudiant | 30 ans, responsable catalogue |
| Recherche des films | Gère les fiches des films |
| Veut trouver rapidement | Veut éviter les erreurs |

**Deux profils, deux besoins différents.**

---

# 4. User Story : définition

Une fonctionnalité exprimée du point de vue utilisateur.

**Structure :**

> En tant que [utilisateur], je veux [action], afin de [bénéfice].

**Exemple :**

En tant que visiteur, je veux rechercher un film afin de le retrouver rapidement.

---

# 5. User Stories — Visiteur

**US01 — Catalogue**  
Consulter les films pour découvrir le catalogue.

**US02 — Recherche**  
Rechercher par titre pour retrouver un film.

**US03 — Filtre**  
Filtrer par genre pour explorer une catégorie.

---

# 6. User Stories — Visiteur et administrateur

**US04 — Détails**  
Consulter la fiche d'un film pour connaître ses informations.

**US05 — Gestion**  
Ajouter, modifier et supprimer un film pour garder le catalogue à jour.

---

# 7. Critères d'acceptation

Ils définissent comment vérifier une User Story.

**Exemple — Recherche :**

- Le visiteur saisit tout ou partie d'un titre.
- Seuls les films correspondants sont affichés.
- Sans résultat, un message apparaît.

**Un critère doit être concret et testable.**

---

# 8. MVP — Première version

**Inclus :**

- Catalogue et fiche détaillée
- Recherche par titre et filtre par genre
- Gestion des fiches de films

**Objectif :** fournir une première version utile.

---

# 9. Évolutions futures

- Comptes et profils visiteurs
- Favoris, notes et commentaires
- Recommandations personnalisées
- Lecture vidéo en ligne

Ces fonctions ne sont pas nécessaires pour valider le MVP catalogue.

