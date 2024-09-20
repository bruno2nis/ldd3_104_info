---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Interpréteur Python

Un interpréteur Python est une application informatique qui exécute les instructions d'un code source écrit en langage Python. L'exécution d'une instruction peut :
- créer, modifier, supprimer des objets Python (données) dans l'espace des objets en mémoire de la machine
- assigner un objet à un nom
- produire des sorties (à l'écran, dans un fichier, sur le réseau...)
- prendre en compte des entrées (depuis le clavier, un fichier, un réseau...)

```{image} img/interpreteur.png
:width: 360px
:align: center
```

## Rôle d'un interpréteur Python

- **Analyser et exécuter du code** - l'interpréteur lit le code source écrit en Python, le traduit en un code intermédiaire (*bytecode* en anglais), et l'exécute immédiatement.
- **Gérer de la mémoire** - l'interpréteur gère la mémoire en allouant et libérant l'espace nécessaire pour les objets (données) via un mécanisme de ramasse-miettes (*garbage collection* en anglais).
- **Gérer des erreurs** - l'interpréteur identifie les erreurs syntaxiques ou d'exécution et affiche des messages d'erreur appropriés, ce qui facilite le débogage du programme.
- **Fournir un environnement interactif** - l'interpréteur permet aux codeurs de tester du code ligne par ligne dans un environnement interactif, comme le REPL (*Read-Eval-Print Loop*). Cela permet de rapidement tester des idées ou de comprendre comment une partie spécifique du code fonctionne.

## Exemples d'interpréteur Python

Les interpréteurs Python sont parfois appelés implémentations Python, car ils concrétisent les actions portées par la sémantique des instructions décrite dans un code source. Voici quelques exemples :
- **CPython** est l'interpréteur originel et le mieux maintenu, écrit en langage C. Il implémente généralement en premier les nouvelles fonctionnalités du langage au fur et à mesure de la sortie des nouvelles versions.
- **IPython** propose des fonctionnalités telles que l'introspection, une syntaxe additionnelle, la complétion et un historique riche. Le projet Jupyter est une branche devenue autonome du développement de IPython.
- **PyPy** est un interpréteur entièrement codé en langage Python, il est bien adapté pour ceux qui expérimentent de nouvelles fonctionnalités pour langage Python.
- **Jython** est un interpréteur codé en langage Java, il permet d'exécuter du code Python sur la machine virtuelle Java (JVM). Cela facilite l'interopérabilité avec le code Java.
- **MicroPython** est un interpréteur allégé qui se limite à un petit sous-ensemble de la bibliothèque standard Python, afin d'être optimisé pour fonctionner sur des microcontrôleurs et dans des environnements contraints en termes de mémoire et de vitesse de traitement.

Dans le cadre du module de formation, c'est principalement CPython qui sera utilisé de manière transparente à partir de l'interface JupyterLab. Pour connaitre l'identité de l'interpréteur qui exécute un code source, si suffit de lui faire exécuter les deux instructions Python suivantes pour qu'il affiche son nom et sa version.

```{code-cell} ipython3
import platform
print(platform.python_implementation(), platform.python_version())
```

## Fonctionnement d'un interpréteur Python

Le fonctionnement d'un interpréteur Python peut être divisé en plusieurs étapes clés : la lecture du code source, l'analyse lexicale et syntaxique, la traduction en code intermédiaire, l'exécution du code intermédiaire et la gestion de la mémoire.

**1. Lecture du code source**

L'interpréteur commence par lire le code Python, soit depuis un fichier (lorsque vous exécutez un script), soit directement via l'environnement interactif en proposant une invite de commande à l'utilisateur.

Exemple de code source Python

``` python
x = 10 + 3
if x > 5:
    print("x est supérieur à 5")
```

**2. Analyse lexicale et syntaxique du code source**

L'interpréteur analyse ensuite le code source pour vérifier qu'il est valide syntaxiquement. Cette étape commence par transformer le code en une série de lexèmes (*tokens* en anglais), des symboles lexicaux qui représentent les différents éléments du code (mots-clés, identifiants, opérateurs, etc.). 

Exemple avec code source Python précédent, l'analyseur identifie les lexèmes suivants :

- identifiants : `x`, `print`
- mots-clés : `if`
- littéraux : `10`, `3`, `5`, `"x est supérieur à 5"`
- opérateurs : `+`, `>`
- délimiteurs : `=`, `:`, `(`, `)`

Si l'analyse lexicale échoue, l'interpréteur Python renvoie un message d'erreur. Ensuite, il effectue une analyse syntaxique pour vérifier que les règles de syntaxe (la grammaire) du langage Python sont respectées.

Exemples avec code source Python précédent, l'analyseur identifie les deux instructions suivantes :
- l'instruction simple `x = 10 + 3` respecte la syntaxe `<identifiant> = <expression>`, ce qui correspond à l'assignation du résultat de l'`<expression>` au nom `<identifiant>`
- l'instruction composée `if x > 5: print("x est supérieur à 5")` respecte la syntaxe `<clause if>`, elle-même respectant la syntaxe `if <expression_de_test>: <suite>` et avec l'`<expression_de_test>` et `<suite>` respectant leurs propres syntaxes.

Si l'enchainement de lexèmes ne correspond pas à la grammaire du langage, l'analyse syntaxique échoue l'interpréteur Python renvoie un message d'erreur.

**3. Traduction en code intermédiaire (bytecode)**

Une fois le code analysé et validé, l'interpréteur le traduit en une forme intermédiaire appelée *bytecode*. Le bytecode est un ensemble d'instructions qui n'est pas directement exécutable par la machine (le processeur), mais qui est compréhensible par l'interpréteur Python. C'est opération est proche d'une compilation (au sens des langages compilés), mais comme le code intermédiaire n'est pas du code machine, le langage Python reste classé parmi les langages interprétés.
- Ce bytecode est indépendant de la machine, c'est-à-dire qu'il peut être exécuté sur n'importe quelle plateforme informatique pour laquelle un interpréteur Python est disponible.
- Le bytecode est stocké dans des fichiers `.pyc` (Python Compiled)

À titre d'illustration, les octets suivants sont le bytecode du code source Python précédent. Les octets sont exprimés en hexadécimal.

``` none
97 00 64 00 5A 00 65 00 64 01 6B 04 00 00 00 00
72 0D 02 00 65 01 64 02 A6 01 00 00 AB 01 00 00
00 00 00 00 00 00 01 00 64 03 53 00 64 03 53 00
```

Le bytecode peut être désassemblé. Cela revient à convertir le bytecode binaire, compréhensible par l'interpréteur Python, en son équivalent sous forme d'un texte formaté lisible par les humains. La signification des colonnes est : 1. le numéro de la ligne concernée dans le code source, 2. l'adresse de l'opération dans le bytecode, 3. le nom de l’opération, 4. le paramètre de l'opération et 5. l'interprétation du paramètre entre parenthèses. 


```
  0           0 RESUME                   0

  1           2 LOAD_CONST               0 (13)
              4 STORE_NAME               0 (x)

  2           6 LOAD_NAME                0 (x)
              8 LOAD_CONST               1 (5)
             10 COMPARE_OP               4 (>)
             16 POP_JUMP_FORWARD_IF_FALSE    13 (to 44)

  3          18 PUSH_NULL
             20 LOAD_NAME                1 (print)
             22 LOAD_CONST               2 ('x est supérieur à 5')
             24 PRECALL                  1
             28 CALL                     1
             38 POP_TOP
             40 LOAD_CONST               3 (None)
             42 RETURN_VALUE

  2          44 LOAD_CONST               3 (None)
             46 RETURN_VALUE
```

**4. Exécution par la machine virtuelle Python**

Le bytecode est ensuite exécuté par la machine virtuelle Python (PVM, *Python Virtual Machine* en anglais). La machine virtuelle est une partie de l'interpréteur Python qui traduit le bytecode en instructions-machine spécifiques à la plateforme sur laquelle l'interpréteur Python est exécuté. C'est l'étape où le programme effectue réellement ses opérations (création d'objet en mémoire, calculs, affichage à l'écran, etc.).

**5. Gestion de la mémoire et collecte des objets non utilisés**

Pendant l'exécution des instructions du code source, l'interpréteur alloue de la mémoire pour les objets créés (comme les numériques, les listes, les dictionnaires, etc.). Lorsque ces objets ne sont plus utilisés, Python dispose d'un système de ramasse-miette (**garbage collection** en anglais) qui libère automatiquement la mémoire non utilisée, évitant ainsi un accroissement inutile de la mémoire utilisée.

