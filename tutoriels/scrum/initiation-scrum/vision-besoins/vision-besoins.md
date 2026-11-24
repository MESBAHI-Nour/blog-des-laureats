# Vision Produit et expression des besoins — Streamix

## 1. Présentation du projet

**Nom du projet :** Streamix  
**Type :** Plateforme de streaming / catalogue de films  
**Objectif de l'atelier :** définir la valeur du produit, ses utilisateurs cibles, les besoins prioritaires et le périmètre de sa première version.

Streamix permet aux visiteurs de découvrir un catalogue de films, de rechercher un film et de consulter ses informations. Un administrateur peut gérer les fiches des films.

Le modèle de données du projet s'appuie sur trois entités principales :

- **Réalisateur** : représente le réalisateur d'un ou de plusieurs films.
- **Film** : représente un film du catalogue. C'est l'entité principale.
- **Genre cinématographique** : permet de classer les films (action, comédie, drame, etc.).

**Périmètre technique connu du projet :** interface en HTML, JavaScript et Tailwind CSS ; backend en PHP ; communication avec Fetch API ; stockage des données au format JSON.

## 2. Vision Produit

### 2.1. Vision

> Pour les personnes qui souhaitent découvrir des films, **Streamix** est une plateforme simple qui permet de parcourir un catalogue, de rechercher des films et de consulter leurs informations par genre et réalisateur. Elle permet également à l'administrateur de maintenir un catalogue organisé et à jour.

### 2.2. Valeur apportée

- **Pour le visiteur :** trouver plus facilement un film et découvrir les informations disponibles.
- **Pour l'administrateur :** organiser et mettre à jour le catalogue depuis un espace de gestion.

### 2.3. Problème auquel le produit répond

Un visiteur peut avoir du mal à retrouver un film lorsqu'un catalogue est mal organisé ou qu'il ne propose pas de recherche et de filtres. Streamix rassemble les films dans un même catalogue et facilite leur consultation.

## 3. Personas

Les Personas ci-dessous sont des profils fictifs utilisés pour représenter les utilisateurs cibles. Ils servent de base de travail et pourront être validés ou ajustés après des échanges avec de vrais utilisateurs.

### 3.1. Persona 1 — Amine, visiteur

| Élément | Description |
|---|---|
| Profil | Amine, 22 ans, étudiant. Il consulte des catalogues de films pendant son temps libre. |
| Rôle | Visiteur de Streamix. |
| Objectifs | Découvrir les films disponibles, retrouver un film par son titre et consulter ses informations. |
| Besoins | Une navigation simple, une recherche facile et un classement par genre. |
| Contraintes | Il souhaite trouver rapidement un film, sans parcourir manuellement tout le catalogue. |
| Attentes | Des informations lisibles et des résultats compréhensibles. |

**Phrase représentative :** « Je veux trouver rapidement un film qui correspond à mes envies. »

### 3.2. Persona 2 — Sara, administratrice

| Élément | Description |
|---|---|
| Profil | Sara, 30 ans, responsable de la gestion du catalogue. |
| Rôle | Administratrice de Streamix. |
| Objectifs | Ajouter de nouveaux films, corriger les informations existantes et supprimer les fiches qui ne doivent plus apparaître. |
| Besoins | Un formulaire clair et des contrôles pour éviter les informations incomplètes. |
| Contraintes | Elle doit gérer les fiches rapidement et garder les relations entre films, réalisateurs et genres cohérentes. |
| Attentes | Une gestion simple et des messages qui indiquent clairement le résultat d'une action. |

**Phrase représentative :** « Je veux gérer les fiches de films facilement pour garder un catalogue organisé. »

## 4. User Stories

Une User Story décrit un besoin du point de vue de la personne qui utilise le produit. Elle respecte le modèle :

> **En tant que** [type d'utilisateur], **je veux** [fonctionnalité], **afin de** [bénéfice recherché].

Les User Stories suivantes représentent les besoins majeurs retenus pour le premier périmètre de Streamix.

### US01 — Consulter le catalogue

**User Story :**  
En tant que visiteur, je veux consulter le catalogue des films afin de découvrir les films disponibles.

**Critères d'acceptation :**

1. Le catalogue affiche les films enregistrés dans Streamix.
2. Chaque élément du catalogue présente au minimum le titre du film, son réalisateur et son genre lorsqu'ils sont renseignés.
3. Si aucun film n'est enregistré, un message indique que le catalogue est vide.

**Priorité :** Haute — MVP.

### US02 — Rechercher un film par son titre

**User Story :**  
En tant que visiteur, je veux rechercher un film par son titre afin de le retrouver rapidement.

**Critères d'acceptation :**

1. Le visiteur peut saisir tout ou une partie du titre dans un champ de recherche.
2. La liste affiche uniquement les films dont le titre correspond au texte saisi.
3. Si aucun film ne correspond, un message « Aucun film trouvé » est affiché.

**Priorité :** Haute — MVP.

### US03 — Filtrer les films par genre

**User Story :**  
En tant que visiteur, je veux filtrer les films par genre afin de découvrir les films d'une catégorie qui m'intéresse.

**Critères d'acceptation :**

1. Le visiteur peut choisir un genre parmi les genres disponibles.
2. Après le choix d'un genre, seuls les films associés à ce genre sont affichés.
3. Le visiteur peut choisir « Tous les genres » pour retrouver l'ensemble du catalogue.

**Priorité :** Haute — MVP.

### US04 — Consulter les informations d'un film

**User Story :**  
En tant que visiteur, je veux consulter la fiche d'un film afin de connaître ses informations avant de faire mon choix.

**Critères d'acceptation :**

1. Le visiteur peut ouvrir la fiche d'un film depuis le catalogue.
2. La fiche affiche au minimum le titre, le réalisateur et le genre associés au film.
3. Les autres informations renseignées pour ce film sont présentées dans sa fiche.

**Priorité :** Haute — MVP.

### US05 — Gérer les fiches des films

**User Story :**  
En tant qu'administrateur, je veux ajouter, modifier et supprimer des fiches de films afin de maintenir le catalogue à jour.

**Critères d'acceptation :**

1. L'administrateur peut ajouter un film en renseignant les informations obligatoires, dont son titre, son réalisateur et son genre.
2. Si une information obligatoire manque, le film n'est pas enregistré et un message explique ce qui doit être complété.
3. Après l'enregistrement, le nouveau film apparaît dans le catalogue.
4. L'administrateur peut modifier les informations d'un film existant et retrouver les informations mises à jour.
5. Avant une suppression, une demande de confirmation est affichée. Après confirmation, le film n'apparaît plus dans le catalogue.

**Priorité :** Haute — MVP.

## 5. Définition du MVP

Le **MVP (Minimum Viable Product)** est la première version utilisable du produit. Il contient les fonctionnalités indispensables pour apporter une première valeur aux utilisateurs et vérifier que la solution répond à leur besoin.

### 5.1. Fonctionnalités incluses dans le MVP

| Fonctionnalité | Utilisateur concerné | Valeur apportée |
|---|---|---|
| Consulter le catalogue | Visiteur | Découvrir les films disponibles. |
| Rechercher par titre | Visiteur | Retrouver rapidement un film. |
| Filtrer par genre | Visiteur | Parcourir les films par catégorie. |
| Consulter la fiche d'un film | Visiteur | Connaître les informations du film. |
| Ajouter, modifier et supprimer un film | Administrateur | Maintenir le catalogue à jour. |

### 5.2. Fonctionnalités reportées aux versions futures

| Fonctionnalité future | Raison du report |
|---|---|
| Création de comptes et profils visiteurs | Non indispensable pour valider la consultation du catalogue. |
| Liste de favoris | Amélioration du confort d'utilisation. |
| Notes et commentaires | Fonctionnalité communautaire à ajouter après le MVP. |
| Recommandations personnalisées | Nécessite des règles ou des données supplémentaires. |
| Lecture vidéo en ligne | À traiter dans une évolution dédiée, selon les ressources vidéo et les droits de diffusion disponibles. |

**Limite du MVP :** cette première version valide principalement la consultation et la gestion du catalogue. Elle ne constitue pas encore un service complet de diffusion vidéo.

## 6. Synthèse

La vision de Streamix est de rendre la découverte et la consultation des films simples. Les deux Personas principaux sont le visiteur, qui explore le catalogue, et l'administrateur, qui le maintient à jour. Les cinq User Stories définissent les besoins essentiels et leurs critères d'acceptation permettent de vérifier leur réalisation.

Le MVP se concentre sur le catalogue, la recherche, le filtre par genre, la consultation des fiches et la gestion des films. Les fonctions complémentaires seront étudiées dans les versions suivantes.

## 7. Vérification des critères de l'atelier

- [x] Vision Produit claire et orientée vers la valeur utilisateur.
- [x] Deux Personas distincts avec objectifs, besoins et contraintes.
- [x] Cinq User Stories rédigées avec la syntaxe demandée.
- [x] Au moins deux critères d'acceptation vérifiables pour chaque User Story.
- [x] Fonctionnalités du MVP distinguées des évolutions futures.
