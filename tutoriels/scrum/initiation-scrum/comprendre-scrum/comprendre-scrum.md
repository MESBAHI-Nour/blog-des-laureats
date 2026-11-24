# Comprendre l'approche Agile et le cadre Scrum

## 1. Objectif de l'atelier

L'objectif est de comprendre la différence entre une gestion de projet en cascade et une démarche Agile, puis de découvrir comment Scrum organise le travail d'une équipe. Les notions sont illustrées avec une plateforme de streaming consacrée aux films.

Le modèle de données présenté dans cet exemple reste limité aux trois tables principales du projet :

- **Réalisateur**
- **Film** (table principale)
- **Genre cinématographique** (classification)

Aucune autre table n'est ajoutée dans cet exemple.

## 2. Approche Cascade et approche Agile

### 2.1. Approche Cascade (cycle en V)

L'approche Cascade organise le projet en étapes successives. Une étape est généralement terminée avant de passer à la suivante : analyse, conception, développement, tests et livraison.

**Avantages :**
- Les étapes et les documents sont planifiés à l'avance.
- Le déroulement est facile à suivre lorsque les besoins sont stables.

**Limites :**
- Un changement tardif peut coûter cher.
- L'utilisateur voit souvent le résultat complet assez tard.
- Une erreur de compréhension au début peut avoir des conséquences sur la suite.

### 2.2. Approche Agile

L'approche Agile avance par cycles courts. L'équipe réalise une petite partie du produit, la présente, recueille des retours et adapte la suite du travail.

**Avantages :**
- Le produit devient visible progressivement.
- Les retours permettent de mieux répondre aux besoins.
- L'équipe peut adapter les priorités lorsque le contexte évolue.

### 2.3. Différence essentielle

| Cascade | Agile |
|---|---|
| Planification détaillée au début | Planification ajustée régulièrement |
| Étapes successives | Cycles courts et itératifs |
| Validation souvent tardive | Retours fréquents |
| Changements plus difficiles | Changements accueillis et évalués |

Agile ne signifie pas travailler sans plan. L'équipe garde un objectif, mais elle peut adapter le chemin pour l'atteindre.

## 3. Les quatre valeurs du Manifeste Agile

Les valeurs Agile indiquent ce que l'équipe privilégie dans sa manière de travailler. Les éléments de droite gardent de la valeur ; ceux de gauche sont simplement privilégiés.

1. **Les individus et leurs interactions** plutôt que les processus et les outils.  
   La communication et la collaboration entre les personnes sont essentielles.
2. **Un logiciel opérationnel** plutôt qu'une documentation exhaustive.  
   Le résultat fonctionnel est prioritaire, tout en gardant une documentation utile.
3. **La collaboration avec le client** plutôt que la négociation contractuelle.  
   L'équipe échange régulièrement avec le client pour vérifier que le produit répond à son besoin.
4. **L'adaptation au changement** plutôt que le suivi d'un plan.  
   L'équipe peut revoir ses priorités lorsque de nouvelles informations apparaissent.

**Exemple pour la plateforme de films :** si les utilisateurs indiquent que le genre d'un film doit être plus visible dans le catalogue, l'équipe peut ajuster les priorités du prochain Sprint.

## 4. Les trois piliers empiriques de Scrum

Scrum s'appuie sur l'expérience, l'observation et l'adaptation. Ses trois piliers sont :

| Pilier | Définition simple | Exemple dans le projet |
|---|---|---|
| **Transparence** | Le travail et son état sont compréhensibles par tous. | Le Product Backlog et l'avancement des fonctionnalités sont visibles par l'équipe. |
| **Inspection** | Le produit et la manière de travailler sont vérifiés régulièrement. | Pendant la Sprint Review, l'équipe montre le catalogue des films et recueille les retours. |
| **Adaptation** | L'équipe ajuste le travail lorsqu'un problème ou une amélioration est identifié. | Après les retours, l'équipe améliore l'affichage des informations sur les films dans un Sprint suivant. |

## 5. Les trois rôles (responsabilités) Scrum

Scrum définit trois responsabilités principales au sein de la Scrum Team.

### 5.1. Product Owner

Il maximise la valeur du produit et s'occupe de la gestion efficace du Product Backlog. Il clarifie le besoin et ordonne les éléments selon leur priorité.

**Exemple :** il donne la priorité à la consultation du catalogue avant des améliorations moins urgentes.

### 5.2. Scrum Master

Il aide l'équipe à comprendre et à appliquer Scrum. Il favorise son efficacité et aide à traiter les obstacles qui empêchent son avancement.

**Exemple :** il facilite les échanges et aide l'équipe à résoudre un blocage qui retarde l'affichage des films.

### 5.3. Développeurs

Ils créent l'incrément utilisable à chaque Sprint. Ils organisent leur travail et choisissent comment réaliser les éléments sélectionnés.

**Exemple :** ils développent l'interface du catalogue et l'affichage des informations liées à chaque film.

> Les rôles ne sont pas trois niveaux hiérarchiques. Ils ont des responsabilités différentes et travaillent ensemble dans une seule Scrum Team.

## 6. Les cinq événements Scrum

Le **Sprint** est l'événement conteneur. Il regroupe les quatre autres événements et toutes les activités nécessaires pour atteindre l'objectif du Sprint.

| Événement | Quand ? | Objectif |
|---|---|---|
| **1. Sprint** | Période fixe d'un mois maximum | Créer un incrément de valeur et atteindre un objectif de Sprint. |
| **2. Sprint Planning** | Au début du Sprint | Définir pourquoi le Sprint est utile, ce qui sera réalisé et comment le travail sera organisé. |
| **3. Daily Scrum** | Chaque jour ouvré du Sprint, 15 minutes maximum | Inspecter l'avancement vers l'objectif et adapter le plan de travail. |
| **4. Sprint Review** | Vers la fin du Sprint | Examiner le résultat avec les parties prenantes et discuter des adaptations à venir. |
| **5. Sprint Retrospective** | Après la Sprint Review et avant le Sprint suivant | Définir des améliorations pour la qualité et l'efficacité de l'équipe. |

**À retenir :** le Daily Scrum n'est pas une réunion de compte rendu destinée au Scrum Master. Les Développeurs l'utilisent pour organiser leur travail et progresser vers l'objectif du Sprint.

## 7. Incrément et Definition of Done (DoD)

### 7.1. Incrément

Un incrément est une partie du produit qui fonctionne, respecte la Definition of Done et peut être utilisée. Il s'ajoute aux incréments précédents.

**Exemple :** à la fin du premier Sprint, un visiteur peut consulter un catalogue de films et voir les informations disponibles sur chaque film, notamment son réalisateur et son genre lorsque les relations sont définies dans le modèle.

### 7.2. Definition of Done

La **Definition of Done (DoD)** est une description commune du niveau de qualité exigé pour qu'un élément soit considéré comme terminé.

Pour le premier incrément de la plateforme de films, une DoD possible est :

- Le catalogue s'affiche sans erreur.
- Les informations affichées proviennent des données du projet.
- Les associations Film–Réalisateur et Film–Genre sont affichées correctement, selon le modèle défini.
- L'affichage reste utilisable sur ordinateur et sur mobile.
- Les critères d'acceptation définis pour l'élément sont respectés.
- Les vérifications prévues par l'équipe sont réussies.
- Le code est intégré au produit et vérifié par l'équipe.

La DoD est un standard de qualité partagé. Elle doit être connue de toute l'équipe et appliquée à chaque incrément.

## 8. Application de Scrum à la plateforme de streaming / Films

### 8.1. Vision du produit

Permettre aux utilisateurs de découvrir un catalogue de films, de consulter les informations disponibles et de retrouver les films par leur réalisateur ou leur genre cinématographique.

### 8.2. Les trois entités principales

| Table | Rôle dans le projet |
|---|---|
| **Film** | Entité principale : représente les films du catalogue. |
| **Réalisateur** | Contient les informations relatives aux réalisateurs. |
| **Genre cinématographique** | Sert à classer les films par genre. |

Les associations précises entre ces tables doivent suivre le modèle de données réellement défini dans le projet.

### 8.3. Exemple de Product Backlog

Le Product Backlog est une liste ordonnée et évolutive des besoins du produit. Voici des exemples d'éléments possibles :

| Priorité indicative | Besoin utilisateur |
|---|---|
| 1 | En tant que visiteur, je veux consulter le catalogue des films afin de découvrir les films disponibles. |
| 2 | En tant que visiteur, je veux consulter les informations d'un film afin de mieux le connaître. |
| 3 | En tant que visiteur, je veux identifier le réalisateur et le genre d'un film afin de mieux comprendre son contenu. |

Ces éléments sont des exemples à confirmer et à détailler avec le Product Owner.

### 8.4. Exemple du premier Sprint

**Durée proposée pour l'exemple :** une semaine. La durée réelle doit être choisie par l'équipe et rester fixe pendant le Sprint.

**Objectif du Sprint :** permettre au visiteur de consulter un premier catalogue de films avec les informations disponibles.

| Étape | Application au projet |
|---|---|
| Sprint Planning | L'équipe choisit le besoin prioritaire : consulter le catalogue. Elle définit l'objectif et le plan de travail. |
| Daily Scrum | Les Développeurs inspectent chaque jour leur avancement et adaptent leur plan. |
| Travail des Développeurs | Ils réalisent l'affichage du catalogue et vérifient les informations associées aux films. |
| Sprint Review | Ils présentent le catalogue fonctionnel et recueillent les retours. |
| Sprint Retrospective | L'équipe identifie ce qui a bien fonctionné et ce qu'elle doit améliorer. |

**Incrément attendu :** une première version fonctionnelle du catalogue des films. Le visiteur peut voir les films et consulter les informations disponibles, dont le réalisateur et le genre lorsque les relations correspondantes sont définies.

**Limite volontaire du premier Sprint :** cet exemple porte sur la consultation du catalogue. Il ne prétend pas livrer toute la plateforme ni la lecture vidéo en streaming.

## 9. Préparation de la soutenance (5 à 10 minutes)

| Partie | Temps indicatif | À expliquer |
|---|---:|---|
| Introduction | 30 secondes | Présenter Agile, Scrum et le projet de films. |
| Cascade et Agile | 1 minute | Expliquer les différences et l'intérêt des cycles courts. |
| Valeurs et piliers | 1 minute 30 | Présenter les quatre valeurs et les trois piliers avec un exemple. |
| Rôles Scrum | 1 minute | Expliquer les responsabilités du Product Owner, du Scrum Master et des Développeurs. |
| Événements Scrum | 1 minute 30 | Présenter les cinq événements dans le déroulement d'un Sprint. |
| Exemple du premier Sprint | 2 minutes | Expliquer l'objectif, le travail et l'incrément du catalogue. |
| Conclusion | 30 secondes | Rappeler l'intérêt du feedback et de l'amélioration continue. |

### Exemple de conclusion orale

« Pour notre plateforme de streaming consacrée aux films, Scrum nous permet d'avancer progressivement. Au premier Sprint, nous pouvons livrer un catalogue fonctionnel qui présente les films et les informations disponibles sur leurs réalisateurs et leurs genres. Nous montrons le résultat, nous recueillons les retours, puis nous adaptons le travail du Sprint suivant. »

## 10. Sources de référence

- [Manifeste pour le développement Agile de logiciels](https://agilemanifesto.org/iso/fr/manifesto.html)
- [Le Guide Scrum — version officielle en français](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-French.pdf)
