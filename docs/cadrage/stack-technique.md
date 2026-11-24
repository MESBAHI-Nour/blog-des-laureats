# Dossier technique — Arguments comparatifs des choix technologiques

## Introduction

La stack technique du **Blog des Lauréats** est définie à partir des besoins de la note de cadrage : présenter les réussites et les expériences des anciens apprenants, permettre la consultation des articles publiés, proposer un espace d'administration sécurisé et offrir une lecture confortable sur ordinateur comme sur mobile.

Le projet retient principalement une **application Laravel rendue côté serveur**, avec une base de données relationnelle. Cette architecture monolithique est adaptée au périmètre actuel : elle rassemble les fonctionnalités dans un même projet, facilite la maintenance et évite d'introduire une architecture distribuée plus complexe que nécessaire.

Pour la consultation nomade, le projet prévoit également une application Android construite avec **NativePHP for Mobile**. L'objectif est de mutualiser autant que possible le code Laravel tout en adaptant l'interface mobile aux composants natifs disponibles.

## 1. Analyse des exigences techniques

Les exigences suivantes découlent des objectifs du Blog des Lauréats et orientent les choix technologiques.

| Exigence | Besoin du projet | Réponse technique retenue |
| --- | --- | --- |
| Performance | Afficher rapidement les listes et les détails des articles | Pagination, requêtes Eloquent ciblées, index MySQL et optimisation des ressources frontend |
| Modularité | Faire évoluer les articles, les catégories, les profils et l'administration sans mélanger les responsabilités | Architecture MVC Laravel, modèles, contrôleurs, services si nécessaire et migrations |
| Sécurité | Protéger les comptes, les formulaires et les actions de publication | Authentification, middleware, validation Laravel, protection CSRF, échappement Blade et requêtes paramétrées |
| Ergonomie responsive | Conserver une lecture confortable sur ordinateur, tablette et téléphone | Tailwind CSS et composants Preline UI testés sur plusieurs tailles d'écran |
| Accès nomade | Permettre la consultation des articles depuis un appareil Android | Application mobile NativePHP avec un parcours centré sur la lecture |
| Maintenabilité | Faciliter le travail en équipe et les évolutions par sprint | Git, conventions Laravel, tests automatisés et revue du code |

Ces choix visent une performance suffisante pour le volume et les usages prévus. Ils ne remplacent pas des mesures : le temps de chargement, les requêtes et l'expérience sur mobile devront être vérifiés pendant les tests et la recette.

## 2. Framework Backend & Socle Unifié (Laravel)

**Laravel** est retenu plutôt qu'un développement PHP sans framework ou qu'un framework minimaliste. Il fournit une structure commune pour organiser les fonctionnalités, sécuriser les traitements et accélérer le développement.

### Arguments comparatifs

| Critère | Laravel | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Organisation | Architecture MVC séparant modèles, vues et contrôleurs | Les données, les traitements et les interfaces sont organisés dans des responsabilités distinctes. |
| Accès aux données | ORM Eloquent et Query Builder | Les articles, auteurs, catégories et statuts sont manipulés avec des modèles et des relations lisibles. |
| Interfaces | Moteur de templates Blade | Les pages web sont composées avec des layouts, des composants et des vues réutilisables. |
| Sécurité | Middleware, validation, protection CSRF et échappement Blade par défaut | Les routes et les formulaires peuvent être protégés de façon cohérente. |
| Requêtes SQL | Eloquent et Query Builder utilisent des requêtes paramétrées dans les usages habituels | Le risque d'injection SQL est réduit lorsque l'équipe évite de construire du SQL brut avec des entrées utilisateur. |
| Évolution de la base | Migrations déclaratives et versionnées | Les changements du schéma sont suivis dans Git et peuvent être rejoués dans les environnements du projet. |
| Tests | Intégration avec PHPUnit et possibilité d'utiliser Pest | Les règles métier et les parcours HTTP peuvent être vérifiés automatiquement. |
| Productivité | Artisan, conventions, injection de dépendances et outils intégrés | L'équipe évite de réécrire les fonctions communes et peut avancer par incréments. |

Laravel fournit aussi les middleware nécessaires pour contrôler l'accès aux routes. Par exemple, les routes d'administration peuvent être réservées aux utilisateurs authentifiés et autorisés, tandis que les visiteurs peuvent consulter uniquement les articles publiés.

La sécurité ne dépend toutefois pas du framework seul. L'équipe doit appliquer la validation côté serveur, vérifier les autorisations dans chaque action sensible, protéger les secrets et éviter l'affichage de HTML non fiable. L'échappement Blade réduit les risques XSS dans les sorties ordinaires, mais l'utilisation de contenu HTML brut exige des précautions supplémentaires.

**Choix retenu :** Laravel constitue le socle backend commun du site web et du projet mobile NativePHP. Les modèles, les règles métier et les traitements compatibles peuvent être mutualisés, sans supposer que toutes les interfaces web seront réutilisées telles quelles sur mobile.

## 3. Persistance des Données (MySQL)

Le projet retient **MySQL** comme système de gestion de base de données relationnelle. Ce choix correspond à la nature des données du blog et aux relations entre les utilisateurs, les auteurs, les articles, les catégories et les statuts de publication.

### Arguments comparatifs

| Critère | MySQL relationnel | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Modélisation | Tables, clés primaires et relations | Les entités du blog sont représentées par un schéma structuré. |
| Intégrité | Clés étrangères et contraintes | Un article peut être relié à un auteur existant et les associations invalides sont limitées par la base. |
| Transactions | Moteur InnoDB et propriétés ACID | Les opérations liées peuvent être validées ensemble ou annulées en cas d'échec. |
| Performance | Index et requêtes SQL | Les recherches, filtres et listes paginées peuvent être optimisés selon les usages réels. |
| Intégration PHP | Pilote PDO et connexion Laravel | Eloquent communique avec MySQL à travers une interface standard prise en charge par PHP. |
| Écosystème | Système largement documenté et utilisé | L'équipe dispose d'une documentation et d'outils connus pour le développement et l'exploitation. |

Avec **InnoDB**, MySQL prend en charge les transactions ACID : atomicité, cohérence, isolation et durabilité. Ces propriétés contribuent à protéger les opérations qui doivent rester cohérentes, par exemple la création d'un article et l'enregistrement de ses relations.

Une base relationnelle est plus adaptée qu'une base NoSQL pour le besoin actuel, car les relations et l'intégrité des données sont importantes. Les index seront ajoutés selon les requêtes réellement utilisées, sans indexer toutes les colonnes inutilement.

**Choix retenu :** MySQL avec le moteur InnoDB, relié à Laravel par PDO et Eloquent. L'application mobile ne doit pas se connecter directement au serveur MySQL depuis le téléphone : l'accès aux données publiées doit passer par une communication applicative sécurisée avec le backend.

## 4. Couche Présentation & Design (Tailwind CSS / Preline UI)

La partie web utilise **Tailwind CSS** avec **Preline UI**, intégrés aux vues Blade.

### Arguments comparatifs

| Critère | Tailwind CSS / Preline UI | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Style | Classes utilitaires composables | Les styles peuvent être construits directement dans les vues sans multiplier les feuilles CSS spécifiques. |
| Responsive design | Variantes par points de rupture et approche mobile-first | Les pages s'adaptent progressivement aux écrans de téléphone, tablette et ordinateur. |
| Productivité | Composants et exemples pré-conçus | Les menus, formulaires, cartes et éléments de navigation sont plus rapides à mettre en place. |
| Cohérence visuelle | Classes et composants réutilisables | Les pages du site gardent une présentation homogène. |
| Accessibilité | Composants Preline intégrant des comportements utiles au clavier et des attributs adaptés | L'équipe dispose d'une bonne base, qui doit tout de même être vérifiée dans les pages finales. |
| Intégration | HTML et Blade, avec les ressources frontend gérées par l'outillage du projet | Le site conserve un rendu côté serveur sans imposer une SPA. |

Tailwind CSS permet de commencer par une mise en page adaptée au mobile puis d'ajouter des règles pour les écrans plus larges. Preline UI accélère la réalisation des composants courants, mais son utilisation ne garantit pas automatiquement une conformité complète aux règles d'accessibilité. Les contrastes, les libellés, la navigation au clavier et le comportement avec un lecteur d'écran doivent être contrôlés.

**Choix retenu :** Tailwind CSS assure la composition visuelle et le responsive design ; Preline UI fournit une bibliothèque de composants réutilisables. Les composants seront adaptés à l'identité graphique du Blog des Lauréats et testés sur plusieurs tailles d'écran.

## 5. Réactivité Frontend (Alpine.js)

**Alpine.js** est retenu pour les interactions simples côté navigateur. Il complète Blade sans imposer la structure et la complexité d'une application monopage (SPA).

### Arguments comparatifs

| Critère | Alpine.js | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Syntaxe | Attributs déclaratifs directement dans le HTML | Les comportements restent proches des éléments concernés. |
| Légèreté | Bibliothèque ciblée sur les interactions d'interface | Le projet évite un état global et une architecture frontend lourde pour des besoins simples. |
| Intégration | Fonctionne avec les vues Blade | Les interactions complètent le HTML généré par Laravel. |
| Usages | Menus, modales, accordéons, affichage conditionnel et petits filtres | Les pages deviennent plus agréables sans déplacer les règles métier dans le navigateur. |
| Maintenance | Peu de structure supplémentaire pour des comportements limités | Les interactions restent faciles à localiser et à modifier. |

Alpine.js peut gérer l'ouverture d'un menu, l'affichage d'une fenêtre modale ou un accordéon. En revanche, Laravel reste responsable de la validation, des autorisations, des règles métier et de l'enregistrement des données. Une vérification côté serveur reste obligatoire, même lorsqu'un contrôle existe dans le navigateur.

**Choix retenu :** Alpine.js est utilisé uniquement lorsque l'interface a besoin d'une interaction dynamique légère. Il ne remplace ni Laravel ni les contrôles de sécurité du backend.

## 6. Développement & Déploiement Mobile (NativePHP for Mobile)

Le projet retient **NativePHP for Mobile** pour préparer une application Android consacrée à la consultation et à la lecture des articles du Blog des Lauréats.

Documentation officielle : <https://nativephp.com/docs/mobile/4/getting-started/introduction>.

### Principe technique

NativePHP for Mobile permet d'exécuter une application PHP/Laravel sur un appareil mobile en intégrant un runtime PHP précompilé dans l'application native. Le package fournit également les mécanismes de communication avec les fonctions natives de la plateforme. La documentation NativePHP décrit un shell natif Android/iOS qui embarque le runtime PHP avec le code de l'application, sans nécessiter un serveur web local sur le téléphone.

Avec son système **EDGE**, NativePHP transforme des composants écrits avec la syntaxe Blade en éléments d'interface natifs. Les écrans mobiles peuvent donc rester dans l'écosystème Laravel et utiliser des composants Blade adaptés au rendu natif.

### Arguments comparatifs

| Critère | NativePHP for Mobile | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Exécution | Runtime PHP intégré à l'application mobile | Le code PHP compatible peut être exécuté sur l'appareil sans serveur PHP local. |
| Socle applicatif | Intégration avec Laravel | Les modèles, services, validations et règles métier compatibles peuvent être mutualisés avec le projet web. |
| Interface | Composants EDGE définis avec Blade et rendus en éléments natifs | L'équipe peut conserver la syntaxe Blade tout en créant des écrans adaptés au mobile. |
| Maintenance | Projet mobile dans l'écosystème PHP/Laravel | La nécessité d'entretenir une seconde stack complète en Flutter ou React Native est réduite. |
| Périmètre | Écrans limités à la consultation des articles | Le développement se concentre sur la liste des articles, les détails, les catégories et la lecture. |

### Mutualisation et limites à prévoir

L'objectif est de **réutiliser au maximum la logique applicative Laravel**, notamment les modèles, les services, les règles de validation et les traitements communs. Il ne faut cependant pas promettre une réutilisation automatique de 100 % du code et de toutes les vues web : une interface web HTML classique et une interface mobile native n'ont pas exactement les mêmes composants. Les écrans mobiles devront être adaptés avec les composants EDGE pris en charge par la version de NativePHP utilisée.

Le site web conserve MySQL comme base centrale. Le téléphone ne doit pas recevoir les identifiants MySQL ni ouvrir une connexion directe à la base distante. Pour afficher les derniers articles publiés, l'application mobile devra communiquer avec le backend du Blog des Lauréats par HTTPS, au moyen d'une interface de lecture contrôlée dans le projet Laravel. Cette communication peut réutiliser le backend existant : elle ne nécessite pas de créer un second projet backend indépendant. Le format et les routes de cette communication devront être définis pendant la conception technique.

Une consultation hors ligne ne doit pas être considérée comme acquise automatiquement. Si elle devient nécessaire, il faudra prévoir et tester une stratégie de cache ou de synchronisation locale des articles.

### Comparatif avec une stack mobile séparée

Une solution Flutter ou React Native demanderait de développer et maintenir une application mobile distincte, avec ses propres écrans, sa navigation et une couche de communication avec le backend. Pour un périmètre limité à la lecture des articles, NativePHP est choisi afin de rester proche du socle Laravel et de limiter la duplication. Ce choix devra être confirmé par un prototype Android vérifiant la compatibilité des dépendances Laravel utilisées dans le projet.

**Choix retenu :** NativePHP for Mobile est retenu pour le build Android de consultation. Le code métier compatible est mutualisé ; l'interface mobile est adaptée au rendu natif ; les articles publiés sont récupérés de manière sécurisée depuis le backend central.

## 7. Qualité & Tests Automatisés (TDD et Agent IA)

Le projet applique une démarche **TDD (Test-Driven Development)** pour vérifier le comportement attendu avant ou pendant l'implémentation de chaque fonctionnalité.

### Cycle TDD

1. **Red :** écrire un test qui décrit le comportement attendu et vérifier qu'il échoue.
2. **Green :** écrire le code minimum pour faire réussir le test.
3. **Refactor :** améliorer le code sans changer le comportement, puis relancer les tests.

### Arguments comparatifs

| Critère | TDD et tests automatisés | Conséquence pour le Blog des Lauréats |
| --- | --- | --- |
| Détection | Les tests sont écrits avant l'implémentation | Les erreurs de logique sont détectées tôt. |
| Couverture | Tests unitaires et fonctionnels | Les petites règles métier et les parcours HTTP sont vérifiés. |
| Régression | Tests relancés après les modifications | Une évolution ne doit pas casser une fonctionnalité déjà validée. |
| Livraison | Résultats reproductibles à chaque sprint | L'équipe dispose d'un contrôle avant la revue et la livraison. |

Les scénarios prioritaires sont :

- Afficher uniquement les articles publiés dans l'espace public.
- Consulter le détail d'un article et filtrer par catégorie.
- Empêcher un visiteur non autorisé d'accéder à l'administration.
- Vérifier les règles de validation et les autorisations de publication.
- Vérifier l'affichage et la récupération des articles dans le parcours mobile.

Laravel prend en charge PHPUnit et peut aussi être utilisé avec Pest. La commande de lancement des tests est :

```powershell
php artisan test
```

Pour exécuter un groupe de tests ciblé :

```powershell
php artisan test --filter Article
```

### Utilisation de l'Agent IA copilote

L'Agent IA est utilisé comme **outil d'assistance au développement**, depuis l'environnement de travail Windows et le terminal PowerShell ou l'éditeur configuré par l'équipe. Il peut aider à :

- analyser une demande et proposer un plan d'implémentation ;
- suggérer une structure Laravel conforme aux conventions du projet ;
- proposer des tests unitaires ou fonctionnels ;
- expliquer une erreur et suggérer des pistes de correction ;
- relire un changement ou repérer des oublis possibles.

L'Agent IA ne remplace pas la décision du développeur. Le code généré doit être relu, adapté au projet et vérifié par les tests automatisés. Les résultats doivent aussi être contrôlés manuellement lorsque le comportement visuel ou mobile est concerné. Aucun mot de passe, jeton, clé API ou autre secret ne doit être transmis à l'agent.

## 8. Environnement de Développement

L'environnement de développement retenu est **Windows**, avec **PowerShell** comme terminal principal. Les outils suivants couvrent le développement web, les tests, la gestion des dépendances et la construction mobile Android.

| Outil | Rôle | Justification |
| --- | --- | --- |
| Windows | Système d'exploitation de l'équipe | Environnement de travail retenu pour le projet. |
| PowerShell | Terminal de commande | Exécuter les commandes PHP, Composer, Node.js, NativePHP et Git. |
| PHP | Langage backend et runtime Laravel | Exécuter le code applicatif et les tests. |
| Composer | Gestionnaire de dépendances PHP | Installer Laravel et les packages, dont NativePHP. |
| MySQL | Système de gestion de base de données | Stocker les utilisateurs, profils, articles, catégories et statuts. |
| Node.js et npm | Gestion des ressources frontend | Installer et préparer Tailwind CSS, Preline UI et les ressources JavaScript. |
| Android Studio | Environnement Android | Installer le SDK, créer un émulateur et préparer le build Android. |
| Android SDK et Platform Tools | Outils de compilation et de débogage | Construire l'application et communiquer avec un appareil ou un émulateur via ADB. |
| JDK compatible avec Gradle | Outils Java nécessaires à la chaîne Android | Répondre aux besoins de compilation Android selon les versions installées. |
| 7-Zip | Outil requis sous Windows par l'environnement NativePHP documenté | Satisfaire une dépendance de l'installation NativePHP for Mobile. |
| Git | Versionnement du code | Suivre les modifications, travailler par branches et collaborer. |
| GitHub CLI (`gh`) | Outil complémentaire pour GitHub | Facultatif : gérer les dépôts et les issues depuis PowerShell. |

La documentation NativePHP Mobile v4 indique notamment PHP 8.3 ou supérieur, Laravel 10 ou supérieur, Android Studio 2024.2.1 ou supérieur et un Android SDK API 29 ou supérieur. Sous Windows, elle indique également l'installation de 7-Zip. La version exacte du JDK doit être compatible avec Gradle et la version Android installée ; elle doit être vérifiée au moment de la configuration.

Quelques commandes courantes depuis la racine du projet Laravel :

```powershell
composer install
npm install
php artisan test
git status
```

Pour préparer et lancer l'application NativePHP, après installation et configuration du package conformément à sa documentation :

```powershell
php artisan native:install
php artisan native:run
```

Les exigences et commandes NativePHP pouvant évoluer selon la version, l'équipe doit suivre la documentation correspondant à la version réellement installée.

## Conclusion

La combinaison **Laravel, MySQL, Tailwind CSS, Preline UI et Alpine.js** forme une stack cohérente pour le site web du Blog des Lauréats. Laravel organise les traitements et sécurise les accès ; MySQL garantit la cohérence des données relationnelles ; Tailwind CSS et Preline UI accélèrent la création d'interfaces responsive ; Alpine.js ajoute les interactions légères nécessaires.

Pour le mobile, **NativePHP for Mobile** permet de conserver un socle PHP/Laravel et de produire une application Android avec des interfaces adaptées aux composants natifs. La mutualisation concerne principalement la logique applicative compatible ; les vues mobiles doivent être adaptées et l'accès aux articles centraux doit passer par une communication HTTPS sécurisée avec le backend.

Enfin, le TDD, les tests automatisés, la revue du code et l'utilisation contrôlée de l'Agent IA contribuent à sécuriser les évolutions réalisées au fil des sprints.

## Références documentaires

- Laravel : <https://laravel.com/docs>
- MySQL 8.4 — InnoDB et ACID : <https://dev.mysql.com/doc/refman/8.4/en/innodb-introduction.html> et <https://dev.mysql.com/doc/refman/8.4/en/mysql-acid.html>
- Tailwind CSS — Responsive design : <https://tailwindcss.com/docs/responsive-design>
- Preline UI — Accessibilité : <https://www.preline.co/docs/accessibility.html>
- Alpine.js : <https://alpinejs.dev/start-here>
- NativePHP for Mobile v4 — Introduction : <https://nativephp.com/docs/mobile/4/getting-started/introduction>
- NativePHP for Mobile v4 — EDGE Components : <https://nativephp.com/docs/mobile/4/edge-components/introduction>
- NativePHP for Mobile v4 — Environnement Android : <https://nativephp.com/docs/mobile/4/getting-started/environment-setup>
