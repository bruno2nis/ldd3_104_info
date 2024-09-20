# Fonctions Python

## Introduction

En programmation, une fonction est un bloc de code autonome qui encapsule une tâche spécifique ou un groupe de tâches connexe. Par exemple `len()` est une fonction qui renvoie la longueur de l'argument qui lui a été passé.

```{code-cell} python
li = ["un", "deux", "trois", "quatre"]
len(li)
```

La fonction native `len()` remplit une tâche spécifique. Le code qui accomplit la tâche est défini quelque part, mais vous n'avez pas besoin de savoir où ou même comment le code fonctionne. Tout ce qu'il faut connaitre, c'est l'interface de la fonction :

1. Quels arguments faut-ils (éventuellement) lui fournir ?
2. Quelles valeurs retourne-t-elle (éventuellement) ?

Ensuite, la fonction est appellée en passant les arguments appropriés. L'exécution du code se détourne vers le corps de la fonction. Lorsque la fonction est terminée, l'exécution retourne à l'intruction de code où elle était resté. La fonction peut ou non renvoyer des données. Les fonction définis par l'utilisateur fonctionnent de la même manière.

Les fonctions permettent
- une abstraction et une réutilisabilité
- une modularité en décomposant des opérations complexes en opérations plus simple
- de séparer l'espace de noms global en portées locales pour éviter les confits de noms

## `def` definition d'une fonction utilisateur

Une instruction composée de type définition de fonction ne contient d'une seule clause.

```{figure} img/fonction_01.png
---
width: 250px
align: center
---
Structure de l'instruction composée  `def`
```

Syntaxe 1 :  `def <nom_de_fonction> (<liste_de_paramètres>):  <suite>` (une seule clause)

où
- `def` est un mot-clé (lexème)
- `<nom_de_fonction>` est un identifiant Python (lexème) qui nom la fonction
- `<liste_de_paramètres>` est une liste facultative, séparée par des virgules, de paramètres pouvant être transmis à la fonction
- `<suite>` est le corps de la fonction, une liste d'instructons

Le corps de la fonction est le bloc de code qui est exécuté lorsque la fonction est appelée, il est défini par l'indentation par rapport à l'entête de la clause.

