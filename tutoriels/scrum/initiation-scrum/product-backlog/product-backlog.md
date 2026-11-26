# Atelier Scrum — Créer, estimer et ordonner le Product Backlog

**Projet : Streamix — Plateforme de streaming / Films**  
**Module : M5 — C.351**  
**Thème : Product Backlog, Story Points, MoSCoW, DoR et DoD**

---

## 1. Objectif de l'atelier

L'objectif est de transformer les besoins de Streamix en User Stories organisées, estimées et priorisées. Ce travail permet à l'équipe de savoir quelles fonctionnalités apporteront le plus de valeur et quelles conditions doivent être respectées avant de commencer ou de terminer une story.

Le projet Streamix est organisé autour de trois entités principales :

- **Film** : entité principale du catalogue.
- **Réalisateur** : personne qui réalise un film.
- **Genre cinématographique** : catégorie d'un film.

**Périmètre technique connu :** HTML, JavaScript et Tailwind CSS pour l'interface ; PHP pour le backend ; Fetch API pour la communication ; fichiers JSON pour le stockage.

Les rôles « Visiteur » et « Administrateur » utilisés dans les exemples ci-dessous sont des rôles fonctionnels proposés pour rédiger les stories. Ils sont à confirmer selon le périmètre final du projet.

## 2. Notions fondamentales

### 2.1 Product Backlog

Le Product Backlog est une liste ordonnée et évolutive de tout ce qui peut être nécessaire pour améliorer le produit : fonctionnalités, corrections et améliorations.

Le Product Owner est responsable de son contenu, de sa clarté et de son ordonnancement. Il tient compte de la valeur métier, des besoins des utilisateurs, des risques et des dépendances. Le backlog peut évoluer pendant le projet.

### 2.2 User Story

Une User Story exprime un besoin du point de vue d'un utilisateur. Une formulation simple est :

> En tant que **[rôle]**, je veux **[besoin]** afin de **[valeur / objectif]**.

Une story doit être accompagnée de critères d'acceptation qui permettent de vérifier le résultat attendu.

### 2.3 Story Points et suite de Fibonacci

Les Story Points mesurent l'effort **relatif** d'une User Story. L'équipe compare les stories selon leur complexité, la quantité de travail, les incertitudes et les vérifications nécessaires.

Pour cet atelier, l'échelle utilisée est :

| Story Points | Interprétation indicative |
|---:|---|
| 1 | Très simple, peu d'incertitude |
| 2 | Simple |
| 3 | Effort moyen |
| 5 | Complexe, plusieurs éléments à traiter |
| 8 | Très complexe ou incertaine ; à examiner et éventuellement découper |

La suite de Fibonacci (1, 2, 3, 5, 8) augmente progressivement les écarts entre les estimations. Plus une story est incertaine, moins l'équipe doit prétendre connaître précisément son effort.

**Les Story Points ne sont pas des heures ni des jours.** Ils ne donnent pas une durée ferme. Après plusieurs Sprints, l'équipe peut observer sa vélocité, c'est-à-dire le nombre de points réellement terminés par Sprint, pour mieux préparer les Sprints suivants.

### 2.4 Méthode MoSCoW

MoSCoW classe les besoins selon leur importance pour une version du produit :

| Priorité | Signification | Règle de décision |
|---|---|---|
| **Must Have** | Indispensable | Sans cette story, le produit ne répond pas à son objectif minimum. |
| **Should Have** | Important | Forte valeur, mais le produit peut fonctionner sans elle au départ. |
| **Could Have** | Souhaitable | Amélioration utile si la capacité le permet. |
| **Won't Have (pour cette version)** | Non retenu maintenant | Hors du périmètre de la version actuelle ; peut être réévalué plus tard. |

Le **MVP (Minimum Viable Product)** est une première version minimale utilisable qui apporte une valeur réelle. Il contient les fonctionnalités indispensables, et non toutes les idées possibles.

### 2.5 DoR et DoD

- **DoR — Definition of Ready :** conditions à respecter pour qu'une User Story soit suffisamment claire et préparée avant son entrée dans un Sprint.
- **DoD — Definition of Done :** conditions de qualité à respecter pour considérer une User Story comme terminée et intégrée au produit.

La DoR répond à : **« Peut-on commencer cette story ? »**  
La DoD répond à : **« Le travail est-il réellement terminé ? »**

## 3. Product Backlog de Streamix

Les estimations ci-dessous sont des estimations initiales proposées pour l'exercice. En Scrum, elles doivent être discutées et validées par l'équipe qui réalisera le travail. L'ordre tient compte de la priorité MoSCoW, de la valeur métier et des dépendances.

| Ordre | ID | User Story | Valeur métier | Estimation | MoSCoW |
|---:|---|---|---|---:|---|
| 1 | US01 | En tant que visiteur, je veux consulter le catalogue des films afin de découvrir les films disponibles. | Donner accès au contenu principal de Streamix. | 3 SP | Must |
| 2 | US02 | En tant que visiteur, je veux consulter la fiche d'un film afin de connaître ses informations. | Aider le visiteur à choisir un film. | 2 SP | Must |
| 3 | US03 | En tant qu'administrateur, je veux ajouter un film afin d'enrichir le catalogue. | Permettre la mise à jour du contenu du catalogue. | 5 SP | Must |
| 4 | US04 | En tant qu'administrateur, je veux modifier les informations d'un film afin de corriger ou actualiser sa fiche. | Maintenir des informations fiables. | 3 SP | Should |
| 5 | US05 | En tant qu'administrateur, je veux supprimer un film afin de retirer un contenu qui ne doit plus apparaître. | Garder un catalogue à jour. | 2 SP | Should |
| 6 | US06 | En tant que visiteur, je veux filtrer les films par genre afin de trouver plus facilement un film qui m'intéresse. | Faciliter la découverte des films. | 3 SP | Should |
| 7 | US07 | En tant que visiteur, je veux consulter les films d'un réalisateur afin de découvrir ses réalisations. | Valoriser les réalisateurs et faciliter l'exploration. | 2 SP | Could |
| 8 | US08 | En tant que visiteur, je veux recevoir des recommandations personnalisées afin de découvrir des films adaptés à mes goûts. | Proposer une découverte personnalisée. | 8 SP | Won't Have — version actuelle |

### 3.1 Critères d'acceptation des stories du MVP

Ces critères rendent les stories Must vérifiables. Ils peuvent être détaillés avec le Product Owner avant le Sprint.

**US01 — Consulter le catalogue (3 SP)**

- La page affiche les films enregistrés dans les données JSON.
- Chaque élément présente au minimum le titre du film.
- Un état compréhensible est affiché si le catalogue est vide ou si les données ne peuvent pas être chargées.

**US02 — Consulter la fiche d'un film (2 SP)**

- Le visiteur peut ouvrir la fiche d'un film depuis le catalogue.
- La fiche affiche les informations disponibles pour ce film.
- Un message adapté apparaît si le film demandé n'existe pas.

**US03 — Ajouter un film (5 SP)**

- L'administrateur peut saisir les informations prévues pour un film.
- Les champs obligatoires sont contrôlés avant l'enregistrement.
- Après un ajout valide, le film est enregistré dans les données JSON.
- Le nouveau film apparaît dans le catalogue.
- Un message indique le succès ou l'échec de l'opération.

## 4. MVP proposé pour le Sprint 1

Pour construire une première version utilisable, le MVP proposé retient les trois stories Must :

| ID | Fonctionnalité | Points |
|---|---|---:|
| US01 | Consulter le catalogue des films | 3 |
| US02 | Consulter la fiche d'un film | 2 |
| US03 | Ajouter un film | 5 |
| | **Total estimé du périmètre MVP** | **10 SP** |

Ce périmètre permet de consulter le catalogue, d'ouvrir une fiche et d'enrichir le contenu. Les stories Should et Could pourront être prises en compte ensuite, selon la valeur et la capacité de l'équipe.

**Attention :** 10 SP est le total estimé du périmètre proposé, pas une garantie que tout pourra être terminé pendant le Sprint 1. Le Product Owner et l'équipe doivent vérifier la capacité réelle du Sprint et la DoR de chaque story avant de s'engager.

## 5. Definition of Ready (DoR)

Une User Story est considérée comme **Ready** lorsque les critères suivants sont vérifiés :

| N° | Critère vérifiable | Validation |
|---:|---|---|
| 1 | La story suit une formulation compréhensible : rôle, besoin et objectif. | ☐ |
| 2 | La valeur métier est expliquée. | ☐ |
| 3 | Les critères d'acceptation sont écrits et vérifiables. | ☐ |
| 4 | Le périmètre est clair ; les ambiguïtés importantes sont levées. | ☐ |
| 5 | Les dépendances et les données nécessaires sont identifiées. | ☐ |
| 6 | L'équipe comprend la story et peut poser ses questions. | ☐ |
| 7 | L'effort a été estimé collectivement en Story Points. | ☐ |
| 8 | La story est suffisamment petite pour être réalisée dans un Sprint. | ☐ |

**Règle :** si un critère essentiel manque, la story reste dans le Product Backlog et est clarifiée avant d'être sélectionnée pour un Sprint.

## 6. Definition of Done (DoD)

Une User Story est considérée comme **Done** uniquement lorsque les critères suivants sont vérifiés :

| N° | Critère vérifiable | Validation |
|---:|---|---|
| 1 | Le développement prévu dans la story est terminé. | ☐ |
| 2 | Tous les critères d'acceptation sont respectés. | ☐ |
| 3 | Les contrôles fonctionnels prévus ont été exécutés avec succès. | ☐ |
| 4 | Les données JSON sont correctement lues ou mises à jour selon le besoin. | ☐ |
| 5 | Les erreurs et les cas attendus (données absentes ou invalides) sont traités. | ☐ |
| 6 | L'interface reste utilisable sur les tailles d'écran ciblées. | ☐ |
| 7 | Aucun défaut bloquant connu ne reste sur la fonctionnalité. | ☐ |
| 8 | Le code est relu et intégré à la version commune du projet. | ☐ |
| 9 | Les informations utiles à la prise en main sont mises à jour si nécessaire. | ☐ |

**Règle :** une story incomplète ou dont les critères ne sont pas vérifiés ne peut pas être déclarée Done.

## 7. Conclusion

Le Product Backlog de Streamix transforme les besoins en un plan de travail ordonné. Les Story Points aident l'équipe à comparer les efforts, MoSCoW permet d'identifier les fonctionnalités prioritaires et le MVP, tandis que la DoR et la DoD définissent les conditions de préparation et de qualité.

Le backlog reste évolutif : le Product Owner peut le réordonner lorsque les besoins, les retours ou les priorités changent.
