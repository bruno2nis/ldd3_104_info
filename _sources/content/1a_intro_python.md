```{note}
En construction
```


# Langage Python

- mots-clés
- primitives
- identifiants
- fonctions natives
- instructions (simples, composées)
- modules

## Programme Python

Programme python construit à partir de blocs de code

Un bloc de code est morceau de texte de programme Python qui est exécuté en tant qu'unité : une liste d'instruction, un module, un corps de fonction ou une définition de classe. 

Chaque commande écrite dans l'interpréteur interactif de Python est un bloc de code

Un bloc de code est exécuté dans un cadre d'exécution

Un cadre d'exécution contient des informations administratives (utilisées pour le débogage) et détermine où et comment l'exécution se poursuit après la fin de l'exécution du bloc de code


- Atomes
    - Identifiants (nom d'un object Python)
    - Littéraux (valeurs constantes de certains types natifs)
    - Forme paranthésée (liste optionnelles d'expression)
    - Agencements de listes
    - agencements d'ensembles
    - agencements de dictionnaires
    - expressions génératrices
    - expressions `yeild from`

- Primaire
    - Références à des attributs 
    - sélections (ou indiçages)
    - Tranchages
    - Appel 


Instructions
- instructions simples
    - expressions
        - opérations arithmétiques (`+`, `-`, `*`, `/`, `**`, `//`, `%`, `@`)
        - opérations bit à bit (`&`, `|`, `^`, `<<`, `>>`)
        - comparaisons
            - comparaisons de valeur (`<`, `>`, `==`, `>=`, `<=`, `!=`)
            - tests d'appartenance (`in`, `not in`)
            - comparaisons d'identifiants (`is`, `is not`)
            - opérations booléennes
    - assignations (ou affectation)
        - simples (`=`)
        - augmentées (`+=`, `-=` , `*=` , `@=` , `/=` , `%=` , `&=` , `|=` , `^=` , `<<=` , `>>=` , `**=` , `//=`)
    - sortie définitive d'une fonction avec éventuellement des valeurs de retours (`return`)
    - sortie temporaire d'une fonction avec éventuellement des valeurs de retours (`yeild`)
    - importation de module (`import`, `from`, `as`)
    - (`raise`, `from`)
    - `pass`, instruction vide qui ne fait rien
    - suppression de la référence à un objet Python (`del`)
    - star_expressions 
    - test de debogage (`assert`)
    - `break`, terminaison prématurée de l'instruction composé *for* ou *while* la plus imbriquée
    - `continue`, terminaison prématurée de l'itération en cours de l'instruction composé *for* ou *while* la plus imbriquée
    - déclaration de noms pointant sur les objects de même nom dans le cadre d'exécution le moins imbriquée de la pile courante (`global`)
    - déclaration de noms pointant pour chacun d'eux sur le premier object portant le même nom en remont la pile courante des cadres d'exécution du plus imbriqué au moins imbriqué(`nonlocal`)
    - instruction future, directive à l'attention de l'interpréteur Python (`from`, `__future__`, `import`, `as`)
    - alias de type (`type`)
- instruction composée
  - définition d'une fonction (`def`)
  - comparaison (`if`, `elif`, `else`)
  - définition d'une classe (`def`)
  - gestionnaire de context (`with`, `as`)
  - itération (`for`, `else`)
  - gestionnaire d'exception (`try`, `except`, `else`, `finally`, `as`)
  - répétition conditionnelle (`while`, `else`)
  - filtrage par motif (`match`, `case`)


## Fonctions natives

### Math

- `abs()` calcule la valeur absolue d'un nombre
- `divmod()` calcule le quotient et le reste de la division entière
- `max()` trouve le plus grand des arguments ou éléments donnés dans un itinéraire
- `min()` trouve le plus petit des arguments ou éléments donnés dans un itinéraire itérable
- `pow()` éleve un nombre à une puissance
- `round()` arrondi une valeur en virgule flottante
- `sum()` somme les valeurs dans un itinéraireable

### Création d'objet de types de base

- `int()`, `float()`, `complex()`, `bool()`

- représenter des nombres entiers : int(), bin(), oct(), and hex()
- Manipulating Other Numbers: float() and complex()
- Building and Representing Strings: str() and repr()
- Processing Boolean Values: bool()
- Encoding Strings: ord() and chr()
- Creating Bytes and Bytearrays: bytes() and bytearray()

### Création objet de type collection
- Creating Lists and Tuples: list() and tuple()
- Constructing Dictionaries: dict()
-  Creating Sets and Frozen Sets: set() and frozenset()

### Processing Iterables and Iterators
- Determining the Number of Items in a Container: len()
- Reversing and Sorting Iterables: reversed() and sorted()
- Determining the Truth Value of Items in Iterables: all() and any()
- Creating Ranges of Integer Values: range()
- Enumerating Items in Loops: enumerate()
- Extracting Slices or Portions of Sequences: slice()
- Zipping Iterables for Parallel Iteration: zip()
- Building and Consuming Iterators: iter() and next()
- Filtering and Mapping Iterables: filter() and map()

### Processing Input and Output
- Accepting Input From the User: input()
- Opening Files: open()
- Printing Text to the Screen or Another Output: print()
- Formatting Strings: format()

### Working With Classes, Objects, and Attributes
- Building Properties: property()
- Creating Class and Static Methods: classmethod() and staticmethod()
- Managing Attributes: getattr(), setattr(), and delattr()
- Checking for Attributes: hasattr()
- Creating and Checking Types: type(), isinstance() and issubclass()
- Checking for Callable Objects: callable()
- Accessing the Parent’s Members: super()
- Building Generic Objects: object()

### Working With Python Scopes
- Inspecting and Updating a Local Scope: locals()
- Inspecting and Updating the Global Scope: globals()

### Introspecting Objects
- Knowing an Object’s Identity: id()
- Checking Names and Attributes: dir() and vars()

### Running Python Code From Strings
- Executing Expressions From Strings: eval()
- Running Code From Strings: exec() and compile()

### Using Miscellaneous Functions
- Accessing the Built-in Help System: help()
- Creating Hash Codes: hash()
- Importing Objects From String Names: __import__()
- Manipulating Binary Data Efficiently: memoryview()


### Essai 

fence python

```{code-block} python
>>> int(1.337)
1
>>> int(+1.1337)
1
>>> int(-1.337)
-1
```

fence python-repl

```{code-block} python-repl
:emphasize-lines: 2,3
:caption: Ce code à ses lignes numérotées
>>> int(1.337)
1
>>> int(+1.1337)
1
>>> int(-1.337)
-1
```

fence {code-block} python

```{code-block} python
:linenos: True
:emphasize-lines: 2,3
:caption: Ce code à ses lignes numérotées
import math
print(math.pi)
print("Hello")
print("world.")
```
