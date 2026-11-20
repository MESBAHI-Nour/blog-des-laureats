# Prompt Engineering & méthode RIO

## 1. Introduction

Les modèles de langage (LLM) sont utilisés pour expliquer des notions, analyser des fichiers et assister les développeurs dans la production de code. Pour obtenir un résultat utile, il faut formuler une demande claire et fournir les bonnes informations.

Le **Prompt Engineering** consiste à concevoir et améliorer les instructions envoyées à un modèle. Le **Context Engineering** consiste à sélectionner et organiser les informations mises à sa disposition.

Objectifs de cette fiche :

- Comprendre le fonctionnement général d'un LLM.
- Identifier les hallucinations et leurs risques.
- Structurer une consigne avec la méthode RIO.
- Connaître les principaux patterns de prompting.
- Comprendre le Context Engineering dans un projet logiciel.
- Comparer Zero-Shot, Few-Shot et l'effet des contraintes.

## 2. Comprendre les LLMs

### 2.1 Définition

Un **LLM** (*Large Language Model*) est un modèle d'intelligence artificielle entraîné sur de grandes quantités de données textuelles et, selon les modèles, de code. Il peut traiter une consigne et générer une suite de texte, du code ou une autre réponse prise en charge.

Exemples de LLMs : GPT, Claude, Gemini et Llama.

### 2.2 Fonctionnement simplifié

Un LLM découpe généralement le texte en unités appelées **tokens**. À partir des tokens déjà présents dans le contexte, il calcule une distribution de probabilités pour le token suivant. Un mécanisme de génération sélectionne ensuite un token. Le processus se répète jusqu'à la fin de la réponse.

Étapes simplifiées :

1. L'utilisateur fournit une consigne et éventuellement du contexte.
2. Le texte est converti en tokens.
3. Le modèle traite les tokens à l'aide de son réseau neuronal.
4. Il estime les probabilités des tokens suivants.
5. Il génère la réponse token après token.

Un LLM ne consulte pas automatiquement la documentation officielle et ne vérifie pas toujours si le code produit peut s'exécuter. La génération probabiliste explique pourquoi une réponse peut sembler convaincante tout en étant incorrecte.

### 2.3 Hallucinations

Une **hallucination** est une information générée par un modèle qui paraît crédible, mais qui est fausse, non vérifiée ou inventée.

Exemples en développement :

- Une méthode ou une fonction qui n'existe pas.
- Un nom de bibliothèque ou une option inventés.
- Une mauvaise utilisation d'une API.
- Une requête SQL qui ne correspond pas au schéma réel.
- Une explication incorrecte d'un message d'erreur.

**Causes possibles :**

- Contexte incomplet ou ambigu.
- Question qui suppose une information inexistante.
- Documentation absente, ancienne ou non fournie.
- Similarité entre plusieurs bibliothèques ou versions.
- Nature probabiliste de la génération.

**Réduction des risques :**

- Fournir la version des outils et les fichiers pertinents.
- Demander au modèle de signaler ses incertitudes.
- Vérifier les informations dans la documentation officielle.
- Exécuter le code et les tests.
- Faire une revue humaine, notamment pour la sécurité.

Une consigne bien écrite réduit certains risques, mais ne garantit jamais une réponse vraie.

## 3. Prompt Engineering

### 3.1 Définition

Le **Prompt Engineering** est la pratique qui consiste à concevoir, tester et améliorer les instructions données à un modèle d'IA afin d'obtenir une réponse adaptée à un objectif.

Dans le développement logiciel, une consigne utile précise notamment :

- Le résultat attendu.
- Le contexte technique et métier.
- Les fichiers ou données à utiliser.
- Les règles et contraintes à respecter.
- Le format de restitution.

### 3.2 Pourquoi l'utiliser ?

- Réduire les ambiguïtés.
- Limiter les réponses hors sujet.
- Respecter les conventions du projet.
- Obtenir un format de sortie régulier.
- Réduire les modifications non souhaitées.
- Faciliter la vérification du résultat.

Le prompt est un moyen de guider le modèle, pas une garantie d'exécution correcte.

## 4. La méthode RIO

RIO est une méthode simple de structuration d'une consigne.

### R — Rôle (Persona)

Décrire le rôle, le domaine d'expertise et la posture attendue.

Exemple :

> Tu es un développeur Laravel expérimenté, spécialisé dans les API REST et la qualité du code.

Le rôle aide à orienter le vocabulaire et le type de réponse. Il ne transforme pas réellement le modèle en expert certifié.

### I — Instruction (contexte et tâche)

Décrire précisément l'action à réaliser, le contexte, les données disponibles et les limites.

Exemple :

> Dans ce projet Laravel, crée une fonctionnalité CRUD pour les catégories. Analyse d'abord les routes, les modèles et les contrôleurs existants. Respecte l'architecture déjà utilisée. Ne modifie pas les autres fonctionnalités et n'ajoute aucune dépendance.

### O — Output (format attendu)

Définir la forme de la réponse ou du livrable.

Exemple :

> Présente un résumé des fichiers à modifier, puis le contenu complet de chaque fichier concerné. Réponds en français simple avec des titres Markdown. Termine par les commandes de test à exécuter.

### Exemple complet RIO

```text
R — RÔLE
Tu es un développeur Laravel expérimenté.

I — INSTRUCTION
Analyse le projet existant et ajoute un CRUD pour les catégories.
Respecte les conventions et les dépendances déjà présentes.
Ne modifie pas les fonctionnalités sans rapport avec la demande.
Ne fais aucun commit.

O — OUTPUT
Présente d'abord un plan court.
Ensuite, indique chaque fichier créé ou modifié et son contenu.
Termine par les tests à exécuter et les points à vérifier.
Réponds en français simple.
```

## 5. Patterns fondamentaux de prompting

Un **pattern** est une technique réutilisable pour structurer une consigne.

### 5.1 Persona Pattern

**But :** préciser le rôle attendu.

```text
Tu es un développeur PHP spécialisé en programmation orientée objet.
Explique la différence entre une interface et une classe abstraite.
```

**Intérêt :** adapter l'explication au domaine et au niveau souhaités.

### 5.2 Template / Format Pattern

**But :** imposer une structure de réponse.

```text
Présente la réponse avec cette structure :
1. Définition
2. Fonctionnement
3. Exemple de code
4. Avantages et limites
5. Conclusion
```

**Intérêt :** obtenir des réponses faciles à lire et à comparer.

### 5.3 Constraint Pattern

**But :** fixer des limites explicites.

```text
Utilise uniquement PHP et MySQL.
N'ajoute aucune bibliothèque.
Ne supprime aucun fichier.
Ne modifie pas les autres fonctionnalités.
Ne fais aucun commit Git.
```

**Intérêt :** réduire les actions non souhaitées. Les contraintes doivent être vérifiées : le modèle peut ne pas toutes les respecter.

### 5.4 Step-by-Step Pattern

**But :** demander une démarche organisée en étapes.

```text
Traite la tâche dans cet ordre :
1. Analyse le besoin.
2. Identifie les fichiers concernés.
3. Propose un plan.
4. Réalise les changements autorisés.
5. Lance ou indique les tests.
6. Résume les résultats.
```

**Intérêt :** rendre une tâche complexe plus facile à suivre. Il est préférable de demander les étapes utiles et une justification synthétique, plutôt que le raisonnement interne détaillé du modèle.

### 5.5 Few-Shot Pattern

**But :** fournir un ou plusieurs exemples du résultat attendu.

```text
Exemple de fonction :
function addition(a, b) {
    return a + b;
}

Crée une fonction multiplication(a, b)
en respectant le même style.
```

**Intérêt :** montrer concrètement le format, le style ou la convention à reproduire.

### 5.6 Reflective Pattern

**But :** demander une vérification du travail et, si nécessaire, une validation avant les changements.

```text
Avant toute modification :
1. Analyse les fichiers concernés.
2. Signale les risques.
3. Propose un plan de modification.
4. Attends ma validation.

Après la modification, vérifie les changements
et indique les tests effectués.
```

**Intérêt :** éviter les changements prématurés et améliorer le contrôle. Une auto-vérification par le modèle ne remplace pas les tests ni la revue humaine.

### 5.7 Récapitulatif

| Pattern | Fonction principale |
|---|---|
| Persona | Définir le rôle |
| Template / Format | Définir la structure |
| Constraint | Définir les limites |
| Step-by-Step | Organiser les étapes |
| Few-Shot | Montrer des exemples |
| Reflective | Faire vérifier le travail |

Ces patterns peuvent être combinés dans un même prompt.

## 6. Context Engineering

### 6.1 Définition

Le **Context Engineering** consiste à sélectionner, organiser et fournir au modèle les informations nécessaires pour accomplir une tâche dans un contexte donné.

Le Prompt Engineering formule principalement la consigne. Le Context Engineering prépare l'ensemble des informations utiles autour de cette consigne.

### 6.2 Exemple dans un projet Laravel

Demande seule :

```text
Crée un CRUD pour les catégories.
```

Cette demande ne précise pas la structure du projet, la version de Laravel, les conventions, le schéma de la base de données ni les fichiers existants.

Contexte mieux préparé :

- Version de Laravel et version de PHP.
- Structure des dossiers concernés.
- Modèle et migration des catégories.
- Routes existantes.
- Contrôleurs et vues similaires.
- Règles métier et conventions du projet.
- Tests existants et critères d'acceptation.

L'agent peut alors adapter sa proposition au projet réel au lieu d'inventer sa structure.

### 6.3 Fenêtre de contexte

La **fenêtre de contexte** représente la quantité de tokens que le modèle peut prendre en compte dans une interaction. Selon le modèle, elle peut contenir les instructions, les messages, les extraits de fichiers et les réponses précédentes.

Si le contexte est trop volumineux ou mal organisé :

- Des informations importantes peuvent ne pas être incluses.
- Des éléments anciens peuvent devenir moins pertinents.
- Le modèle peut confondre des versions ou des règles.
- Le coût et le temps de traitement peuvent augmenter.

### 6.4 Bonnes pratiques

- Fournir uniquement les fichiers utiles à la tâche.
- Donner les versions et les dépendances exactes.
- Présenter les règles du projet dans un document clair.
- Éviter les informations répétées ou contradictoires.
- Découper une grande tâche en petites étapes.
- Actualiser le contexte lorsque le projet évolue.
- Vérifier que l'agent a bien accès aux fichiers mentionnés.

Un modèle ne dispose pas automatiquement de tous les fichiers du projet ni de tous les échanges d'une session précédente. Il faut lui fournir le contexte nécessaire par les moyens disponibles.

## 7. Recherches et expérimentations

Les expériences suivantes doivent être réalisées avec le même modèle et une tâche identique pour comparer les résultats de façon plus juste.

### 7.1 Expérience 1 — Hallucinations et génération de code

**Question :** pourquoi un LLM peut-il générer du code incorrect ?

**Protocole :**

1. Demander au modèle de créer une fonction ou une fonctionnalité.
2. Examiner les classes, méthodes et bibliothèques proposées.
3. Vérifier leur existence dans la documentation officielle.
4. Exécuter le code et lancer des tests.
5. Noter les erreurs et les éléments corrects.

**Exemple de demande :**

```text
En Laravel, crée une méthode qui récupère
les catégories et retourne une réponse JSON.
Indique les fichiers concernés.
```

**Analyse :** le modèle peut produire un code qui paraît valide sans connaître la structure réelle du projet. Une méthode inventée, une mauvaise version d'API ou une dépendance absente peut provoquer une erreur.

**Réponse à la recherche :** la complétion probabiliste produit une suite plausible à partir du contexte ; elle ne constitue pas une preuve de vérité. La vérification par documentation, exécution et tests est donc indispensable.

### 7.2 Expérience 2 — Zero-Shot et Few-Shot

**Zero-Shot :** demander une tâche sans fournir d'exemple.

```text
Écris une fonction JavaScript isEmail(value)
qui vérifie le format d'une adresse email.
```

**Few-Shot :** fournir un exemple de style avant la tâche.

```text
Voici le style à respecter :

function isNumber(value) {
    return typeof value === "number";
}

Crée maintenant une fonction isEmail(value)
qui vérifie le format d'une adresse email.
Garde une structure simple et un nom explicite.
```

**Protocole de comparaison :**

1. Envoyer la demande Zero-Shot.
2. Enregistrer la réponse.
3. Envoyer la demande Few-Shot au même modèle.
4. Comparer la structure, le respect du style et le fonctionnement.
5. Exécuter des tests sur les deux fonctions.

| Critère | Zero-Shot | Few-Shot |
|---|---|---|
| Exemple fourni | Non | Oui |
| Préparation | Rapide | Demande un exemple |
| Style | Plus libre | Guidé par l'exemple |
| Résultat | Peut varier | Peut mieux suivre le modèle |
| Usage | Tâche courante | Convention précise à reproduire |

**Conclusion :** le Zero-Shot est rapide lorsqu'une consigne suffit. Le Few-Shot est utile lorsqu'il faut montrer un style ou un format précis. Un exemple incorrect peut toutefois transmettre une mauvaise convention.

### 7.3 Expérience 3 — Contraintes négatives

**Objectif :** observer si des interdictions explicites limitent les actions non souhaitées.

**Prompt A — Sans contraintes détaillées :**

```text
Crée un CRUD Laravel pour gérer les catégories.
```

**Prompt B — Avec contraintes :**

```text
Crée un CRUD Laravel pour gérer les catégories.

Contraintes :
- Respecte l'architecture existante.
- Ne modifie pas les fonctionnalités sans rapport.
- Ne supprime aucun fichier.
- N'ajoute aucune dépendance.
- Ne fais aucun commit Git.
- Indique tous les fichiers modifiés.
```

**Protocole :**

1. Utiliser le même projet et le même modèle.
2. Exécuter le prompt A et noter les changements.
3. Revenir à l'état initial du projet.
4. Exécuter le prompt B et noter les changements.
5. Comparer les fichiers touchés et les consignes respectées.

| Critère | Prompt A | Prompt B |
|---|---|---|
| Nombre de contraintes | Faible | Plus élevé |
| Liberté de l'agent | Plus grande | Plus encadrée |
| Actions non souhaitées | À observer | À observer |
| Respect du périmètre | Non précisé | Explicitement demandé |

**Conclusion :** les contraintes négatives rendent les limites plus explicites et peuvent améliorer la prévisibilité. Elles ne garantissent pas leur respect : il faut contrôler les modifications et les résultats.

**Important :** les tableaux ci-dessus décrivent le protocole et les tendances possibles, pas des mesures déjà obtenues. Les résultats réels doivent être complétés après les tests.

## 8. Bonnes pratiques pour un agent de développement

Avant de demander une modification à un agent :

1. Expliquer le besoin et le résultat attendu.
2. Définir son rôle et ses limites.
3. Fournir les fichiers et règles utiles.
4. Demander un plan avant une modification importante.
5. Limiter les changements au périmètre demandé.
6. Exécuter les tests et vérifier les fichiers modifiés.
7. Faire une revue humaine avant de valider le travail.

### Exemple de prompt complet

```text
RÔLE
Tu es un développeur PHP expérimenté.

CONTEXTE
Le projet utilise PHP, JavaScript et une base de données MySQL.
La fonctionnalité concerne la gestion des catégories.
Analyse les fichiers existants avant de proposer une solution.

INSTRUCTION
Ajoute les opérations de création, lecture, modification
et suppression des catégories.
Respecte les conventions déjà utilisées dans le projet.

CONTRAINTES
- Ne modifie pas les fonctionnalités sans rapport.
- Ne supprime aucun fichier.
- N'ajoute aucune dépendance.
- Ne fais aucun commit.
- Signale toute information manquante.

OUTPUT
1. Présente un plan court.
2. Liste les fichiers concernés.
3. Donne le contenu complet des fichiers modifiés.
4. Indique les tests à exécuter.
5. Résume les vérifications effectuées.
Réponds en français simple.
```

## 9. Conclusion personnelle

Le Prompt Engineering permet de mieux formuler les demandes adressées à un LLM. La méthode RIO aide à organiser ces demandes autour du rôle, de l'instruction et du résultat attendu. Les patterns apportent des techniques réutilisables pour préciser le style, la structure, les limites et les vérifications.

Le Context Engineering complète cette approche en donnant à l'agent les fichiers, les règles et les informations nécessaires au projet. Dans le développement logiciel, ces pratiques améliorent la qualité du travail produit par l'IA, mais elles ne remplacent ni les tests, ni la documentation, ni la validation du développeur.

## 10. Ressources documentaires

- [OpenAI — Prompt engineering](https://platform.openai.com/docs/guides/prompt-engineering)
- [OpenAI — Tokenizer](https://platform.openai.com/tokenizer)
- [Anthropic — Prompt engineering overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Google Cloud — Introduction to large language models](https://cloud.google.com/ai/llms)
- [Hugging Face — NLP Course](https://huggingface.co/learn/nlp-course/)
- [OWASP — Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

Les documentations et pages peuvent évoluer. Il faut vérifier les versions et les informations au moment de réaliser les expériences.
