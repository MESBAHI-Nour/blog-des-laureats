---
marp: true
theme: default
size: 16:9
paginate: true
---

# Prompt Engineering
## & méthode RIO

**Comprendre les LLMs, le prompting et le Context Engineering**

---

# Plan

1. Comprendre les LLMs
2. Prompt Engineering
3. Méthode RIO
4. Patterns fondamentaux
5. Context Engineering
6. Expérimentations
7. Conclusion

---

# 1. Les LLMs

**LLM = Large Language Model**

- Modèle entraîné sur de grandes quantités de données
- Traite du texte et génère des tokens
- Peut assister les développeurs

Exemples : GPT, Claude, Gemini, Llama.

---

# Comment fonctionne un LLM ?

1. Reçoit une consigne et un contexte
2. Convertit le texte en tokens
3. Calcule les probabilités du token suivant
4. Génère la réponse progressivement

**La génération est probabiliste.**

---

# Les hallucinations

**Définition :** réponse plausible, mais fausse ou inventée.

Exemples en développement :

- Méthode inexistante
- Bibliothèque inventée
- Mauvaise utilisation d'une API
- Code incorrect ou non sécurisé

---

# Réduire les hallucinations

- Fournir un contexte précis
- Vérifier la documentation officielle
- Exécuter le code
- Ajouter des tests
- Faire une revue humaine

**Une réponse convaincante n'est pas toujours vraie.**

---

# 2. Prompt Engineering

**Définition**

Concevoir et améliorer les instructions données à une IA.

**Objectifs**

- Réduire les ambiguïtés
- Préciser le résultat attendu
- Respecter les règles du projet
- Améliorer la qualité des réponses

---

# 3. La méthode RIO

| Élément | Question | Fonction |
|---|---|---|
| R — Rôle | Qui est l'IA ? | Définir l'expertise |
| I — Instruction | Que doit-elle faire ? | Décrire la tâche |
| O — Output | Quel résultat ? | Fixer le format |

**RIO structure une consigne claire.**

---

# RIO : exemple

**R — Rôle**

Développeur Laravel expérimenté.

**I — Instruction**

Créer un CRUD de catégories.
Respecter le projet existant.
Ne pas modifier les autres fonctions.

**O — Output**

Code fichier par fichier.
Explications en français.
Tests à exécuter.

---

# 4. Patterns de prompting

Un pattern est une technique réutilisable.

- **Persona** : définir le rôle
- **Template** : imposer une structure
- **Constraint** : fixer des limites

---

# Autres patterns

- **Step-by-Step** : organiser les étapes
- **Few-Shot** : fournir des exemples
- **Reflective** : vérifier le travail

Les patterns peuvent être combinés.

---

# Few-Shot : exemple

**Sans exemple**

Créer une fonction JavaScript.

**Avec exemple**

Fournir une fonction de référence.
Demander une fonction similaire.

**Résultat attendu :** mieux respecter le style fourni.

---

# 5. Context Engineering

**Définition**

Préparer les informations utiles à la tâche.

Exemple pour un projet Laravel :

- Versions et dépendances
- Modèles et migrations
- Routes et contrôleurs
- Règles métier
- Tests existants

---

# Fenêtre de contexte

Elle contient les tokens traités par le modèle.

- Instructions
- Messages
- Extraits de fichiers
- Réponses précédentes

**Risque :** contexte trop long ou mal organisé.

**Solution :** fournir les informations utiles uniquement.

---

# 6. Expérimentation : Zero-Shot / Few-Shot

**Zero-Shot**

Demander une tâche sans exemple.

**Few-Shot**

Fournir un exemple avant la tâche.

**Comparaison**

- Préparation
- Respect du style
- Structure du code
- Résultat des tests

---

# Expérimentation : contraintes

**Prompt A :** tâche sans limites détaillées.

**Prompt B :** mêmes tâches avec contraintes.

Exemples :

- Ne pas supprimer de fichier
- Ne pas ajouter de dépendance
- Ne pas modifier les autres fonctions
- Ne pas faire de commit

---

# Résultats à observer

Comparer les deux réponses :

- Fichiers modifiés
- Respect des consignes
- Modifications inutiles
- Tests et erreurs

**Une contrainte guide l'agent, mais ne garantit pas son obéissance.**

---

# 7. Bonnes pratiques

1. Définir le rôle
2. Expliquer la tâche
3. Fournir le contexte utile
4. Fixer les contraintes
5. Définir le format attendu
6. Tester et vérifier le résultat

---

# Conclusion

- Le LLM prédit les tokens suivants.
- RIO structure les consignes.
- Les patterns améliorent le prompting.
- Le Context Engineering prépare les informations.
- Les tests restent indispensables.

**L'IA assiste le développeur : elle ne remplace pas sa validation.**

---

# Ressources

- OpenAI — Prompt Engineering
- Anthropic — Prompt Engineering
- Google Cloud — LLMs
- Hugging Face — NLP Course
- OWASP — Top 10 for LLM Applications

Voir les liens dans la fiche technique.
