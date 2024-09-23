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

# Fonctions Python

## Introduction

En programmation, une fonction est un bloc de code autonome qui encapsule une tâche spécifique ou un groupe de tâches connexe. Par exemple `len()` est une fonction qui renvoie la longueur de l'argument qui lui a été passé.

```{code-cell} python
li = ["un", "deux", "trois", "quatre"]
len(li)
```

La fonction native `len()` remplit une tâche spécifique. Le code qui accomplit la tâche est défini quelque part, mais vous n'avez pas besoin de savoir où ou même comment le code fonctionne. Tout ce qu'il faut connaitre, c'est l'interface de la fonction :

1. Quels arguments faut-il (éventuellement) lui fournir ?
2. Quelles valeurs retourne-t-elle (éventuellement) ?

Ensuite, la fonction est appelée en passant les arguments appropriés. L'exécution du code se détourne vers le corps de la fonction. Lorsque la fonction est terminée, l'exécution retourne à l'instruction de code où elle était restée. La fonction peut ou non renvoyer des données. Les fonctions définies par l'utilisateur fonctionnent de la même manière.

Les fonctions permettent
- une abstraction et une réutilisabilité
- une modularité en décomposant des opérations complexes en des opérations plus simples
- de séparer l'espace de noms global en portées locales pour éviter les confits de noms

## Définition d'une fonction (`def`)

Une instruction composée de type définition de fonction ne contient qu'une seule clause.

```{figure} img/fonction_01.png
---
width: 250px
align: center
---
Structure de l'instruction composée  `def`
```

La syntaxe de la définition d'une fonction est

```
def <nom_de_fonction> ( <liste_de_paramètres> ) :  
    <suite>
```

où
- `def` est un mot-clé (lexème)
- `<nom_de_fonction>` est un identifiant Python (lexème) qui nomme la fonction
- `<paramètres>` est une suite facultative de paramètres pouvant être transmis à la fonction, les paramètres sont séparés par des virgules, 
- `<suite>` est le corps de la fonction, il s'agit d'un bloc d'instructions qui doit être non vide et indenté.

Exemple d'une fonction identifiée par le nom `fib`

```{code-cell} python
# ════ début de l'instruction composée ═══╗
#┌───────── début de clause  ───────────┐ ║
def fib(n):               # <-- entête  │ ║
    a, b = 0, 1           # ┐           │ ║
    while a < n:          # ├─ suite    │ ║
        print(a, end=' ') # │  indentée │ ║
        a, b = b, a + b   # │           │ ║
    print()               # ┘           │ ║
#└──────────────────────────────────────┘ ║
# ════════════════════════════════════════╝  
```

## Appel à une fonction

La syntaxe de l'appel à une fonction est 

```
<nom_de_la_fonction> ( <arguments> )
```

où
- `<nom_de_la_fonction>` est l'identifiant de la fonction dans l'espace de nom.
- `<arguments>` est une suite, éventuellement vide, d'arguments à transmettre à la fonction.

L'exécution d'une fonction renvoie un objet qui est déterminé par la manière dont la fonction se termine. 
- si la fonction exécute l'instruction `return`, alors elle se termine et renvoie l'objet à la droite du mot-clé `return` <br />
  Exemple : `return 3` renvoie l'entier `3`,  `return [1, 2]` renvoie la liste `[1, 2]` et `return 1, "b", [4, 5]` renvoie le n-uplet `(1, "b", [4, 5])` (identique à `return (1, "b", [4, 5])`). L'instruction `return` peut apparaitre plusieurs fois dans u
- si l'exécution des instructions du bloc `<suite>` arrive à la fin du bloc avoir exécuté d'instruction `return`, alors elle se termine et renvoie l'objet `None`

::::{grid}
:gutter: 2

:::{grid-item-card} Exemple `factoriel_1()`

``` python
def factoriel_1(n):
    res = 1 
    for i in range(n): 
        res *= i + 1

retour = factoriel_1(4)
print("retour =", retour)
```
``` none
retour = None
```
Lors de l'appel à `factoriel_1()`, aucune instruction `return` n'arrête l'enchainement des instructions du bloc de code de la fonction. Après l'exécution de la dernière instruction du bloc (instruction composée `for`), la fonction se termine et renvoie l'objet `None` à son appelant.
:::

:::{grid-item-card} Exemple `factoriel_2()`
```  python
def factoriel_2(n):
    res = 1 
    for i in range(n): 
        res *= i + 1
    return res

retour = factoriel_2(4)
print("retour =", retour)
```
``` none
retour = 24
```
Lors de l'appel à `factoriel_2()`, l'instruction `return res` arrête l'enchainement des instructions du bloc de code de la fonction et renvoie l'objet `res` (qui ici est l'entier `24`) à son appelant.
:::

::::

## Portée des noms d'objets

Lors de l'exécution d'une instruction, les noms des objets accessibles sont dans un sous-ensemble de l'espace des noms appelés "portée" (*scope* en anglais). Lorsque le nom est accessible, le code peut accéder à l'objet Python qui a été assigné à ce nom.

La structuration de la portée des noms est l'image de la structuration du code source en modules, en fonctions et en sous-fonctions. Ci-dessous un exemple de code avec ses portées de noms associées. La portée du code principale porte généralement le nom "main" tandis que le code d'un module porte le nom du module. Le code principal et ceux des modules sont eux-mêmes inclus dans une portée nommée "Built-in" (portée native) qui contient tous les noms du module builtins (ex: int, float, list, dict, print, abs, pow, ...).


::::{grid}
:gutter: 2

:::{grid-item-card} Exemple de code
```{code-block}
:linenos:
a = "main"

def f1():
    a = "f1"
    b = "b de f1"
    def f1_1():
        a = "f1_1"
        print(a, "voit", b, "et", c)
    print(a, "voit", b, "et", c)
    f1_1()
        
def f2():
    a = "f2"
    print(a, "voit", b, "et", c)
    
b = "b de main"
c = "c de main"
f1()
f2()
print(a, "voit", b, "et", c)
```
:::

:::{grid-item-card} Portées de noms associés

``` none
┌── main ───────────┐ 
│                   │
│ ┌── f1 ─────────┐ │
│ │               │ │
│ │               │ │
│ │ ┌── f1_1 ───┐ │ │
│ │ │           │ │ │
│ │ └───────────┘ │ │
│ │               │ │
│ └───────────────┘ │
│                   │
│ ┌── f2 ─────────┐ │
│ │               │ │
│ └───────────────┘ │
│                   │
│                   │
│                   │
│                   │
│                   │
└───────────────────┘
```
:::

::::

Python distinct quatre types de portées : 

- **Globale** est la portée du code principal (du programme ou du module), celle où il exécute sa 1re instruction
- **Built-in** est la portée native qui englobe la portée globale
- **Locale** est, pour une instruction, la portée où elle se situe (portée relative)
- **Englobante** est la portée qui englobe la portée où se trouve l'instruction.

``` none
┌── Built-in ───────────┐ 
│                       │
│ ┌─ Globale ─────────┐ │
│ │                   │ │
│ │ ┌─ Englobante ──┐ │ │
│ │ │               │ │ │
│ │ │ ┌─Locale ───┐ │ │ │
│ │ │ │           │ │ │ │
│ │ │ └───────────┘ │ │ │
│ │ └───────────────┘ │ │
│ └───────────────────┘ │
└───────────────────────┘
```

Illustration de ces quatre types de portée pour quelques instructions : 

| type de portée | `a = "f1_1"`<br />ligne 7 | `a = "f2"` en ligne 13 | `f1()`<br />ligne 18 
|----------------|----------|----------|----------|
| Locale         | f1_1 (*) | f2       | main     |
| Enblobante     | f1       |          |          |
| Global         | main     | main     | main     |
| Built-in       | builtins | builtins | builtins |

(*) certaines instructions peuvent avoir une succession de portée englobante avant d'atteindre la portée globale

L'interpréteur exécute le code source principal dans une portée englobante appelée builtins qui contient toutes les fonctions natives, les types natifs et les constantes natives.


L'exécution d'une fonction introduit un nouveau sous-espace de nom (table de symboles) utilisé pour stocker les noms locaux créés par la fonction. 

En revanche, les références de variables (noms) sont recherchées dans la table des symboles locaux, puis dans les tables des symboles locaux des fonctions englobantes, puis dans la table des symboles globaux et finalement dans la table des noms natifs (built_in).
 
Par conséquent, bien qu'elles puissent être référencées, il est impossible d'assigner un objet à un nom de la portée globale ou à un nom d'une portée englobante (sauf pour les noms de la portée globale qui apparaissent dans une instruction `global` et sauf pour les  noms des portées englobantes qui apparaissent dans une instruction `nonlocal`).

## Association arguments-paramètres

Au moment de l'appel à une fonction, un objet python doit être assigné à chaque paramètre de la fonction. Cela donne lieu à la création de noms d'objet dans l'espace de nom de la portée **locale** à la fonction.

Pour cela les **arguments** fournis sont associés aux **paramètres** selon différentes stratégie.

### Nombre d'arguments fixe

L'association de base assigne simplement les arguments aux paramètres de même rang, comme l'illustre le tableau suivant.

``` none
Arguments | Paramètres de |       Assignations
 d'appel  |  la fonction  |        à l'appel
----------|---------------|------------------------
 <arg_1>  | <nom_param_1> | <nom_param_1> = <arg_1>
 <arg_2>  | <nom_param_2> | <nom_param_2> = <arg_2>
  .   .   |   .   .   .   |  .   .   .       .   .
 <arg_n>  | <nom_param_n> | <nom_param_n> = <arg_n>

```

Exemple ou les trois arguments passés sont de simples chaines de caractères littérales :

```{code-cell} python
def affiche_salutation(nom, prenom, civilite):
    """Affiche une salutation personnalisée."""
    print("Bonjour", civilite, prenom, nom)


affiche_salutation("Lovelace", "Ada", "Mme")
```

L'appel `affiche_salutation("Lovelace", "Ada", "Mme")` génère les trois assignations suivantes dans la portée locale de la fonction

```{code-block} python
nom = "Lovelace"
prenom = "Ada"
civilité = "Mme"
```


<!--
Puis le block de code de la fonction est exécuté.


Au moment de l'appel à une fonction, les **arguments** fournis sont associés aux **paramètres** attendus par la fonction. La manière de les associer offre de nombreuses possibilité comme les exemples suivants le montre. Ce sont des appels à la même fonction native `print()` avec une grande diversité dans la liste des arguments ; leur nombre est variable, l'argument pour le paramètre `sep` est parfois omis.

```{code-cell} python
print()
print("Bonjour")
print("ens", "paris", "saclay")
print("ens", "paris", "saclay", sep="-")
```

### Association positionnelle

Lorsqu'un argument est un simple objet, c'est un **argument positionnel**. Au moment de l'appel, les arguments positionnels sont associés aux paramètres de même rang.

Exemple ou les trois arguments passés sont de simples chaines de caractères littérales :

```{code-cell} python
def affiche_salutation(nom, prenom, civilite):
    """Affiche une salutation personnalisée."""
    print("Bonjour", civilite, prenom, nom)


affiche_salutation("Lovelace", "Ada", "Mme")
```

Les paramètres peuvent avoir une valeur par défaut, dans ce cas ils n'ont pas besoin d'être associés à un argument au moment de l'appel. Les paramètres sans valeur par défaut sont dits **paramètres positionnels**, les paramètres avec une valeur par défaut sont dits **paramètres positionnels ou nommés**, il suivent la syntaxe suivante dans la définition de la fonction :

`<nom_parametre> = <valeur_par_défaut>`

Dans la définition d'une fonction, après le premier paramètre par défaut, tous les paramètres suivant doivent être aussi par défaut, car l'assossiation positionnelle n'est plus possible.

Exemple d'une fonction avec deux paramètre par défaut `prenom=""` et `civilite=""` :

```{code-cell} python
def affiche_salutation_2(nom, prenom="", civilite=""):
    """Affiche une salutation personnalisée."""
    mots = ["Bonjour"]
    if civilite: 
        mots.append(civilite)
    if prenom: 
        mots.append(prenom)
    mots.append(nom)
    print(" ".join(mots))

affiche_salutation_2("Lovelace", "Ada", "Mme")
affiche_salutation_2("Lovelace", "Ada")  # affiche "Bonjour Ada Lovelace"
affiche_salutation_2("Lovelace") # affiche "Bonjour Lovelace"
```

Dans l'exemple précédant, les appels à la fonction se font avec une association positionnelle, cela oblige à passer le 2e argument si l'on souhaite passer l'argument de civilité qui se place en 3e position.

### Association par nom

Les **arguments nommés** sont les arguments associés explicitement à un paramètre auquel ils doivent être associés en mentionnant le nom du dit paramètre. La syntaxe d'un argument nommées dans l'appel de la fonction est la suivante

 `<nom_parametre> = <argument>`
 
 Dans l'appel à une fonction, après le premier argument nommée, tous les arguments suivant doivent aussi être nommées, car l'association positionnelle n'est plus possible.

Exemple :

```{code-cell} python
affiche_salutation_2("Lovelace", civilite="Ada")
```

## Emballage et déballage

 -->

## Documentation d'une fonction (Docstring)

Toutes les fonctions, comme les modules, les classes et les méthodes, devraient avoir une chaine littérale de caractères comme première instruction. Cette chaine est appelée chaine de documentation (*docstring* en anglais) car elle sert aux outils de documentation du code source comme la fonction native `help()`. En créant un objet de type fonction, l'interpréteur Python lui ajoute l'attribut-donnée `__doc__` qui réfère à cette chaine de documentation.

Il existe des conventions pour l'utilisation de ces chaines de documentation publiées dans les propositions [PEP 8](https://peps.python.org/pep-0008/) et [PEP 257](https://peps.python.org/pep-0257/).

Globalement 
- elles sont placées entre """Trois guillemets"""
- lignes où elles apparaissent doivent avoir une longueur de 72 caractères maximum (espaces vides inclus)

Pour les chaines de documentation à une seule ligne
- tout est sur une seule ligne (guillemets compris)
- le contenu est une phrase qui se termine par un point `.` et qui résume ce que fait la fonction : `Fait ceci.` ou `Fait cela.`

Exemple d'une fonction documentée avec une seule ligne

```{code-cell} python
def racine(a, b, c):
    """Calcul les deux racines d'une équation du second degrés."""
    delta = b**2 - 4 * a * c
    x1 = (-b - delta**0.5) / (2 * a)
    x2 = (-b + delta**0.5) / (2 * a)
    return x1, x2


help(racine)
```

Pour les chaines de documentation multilignes, elles sont composées des éléments suivants
  - une ligne de résumé
  - une ligne vide
  - Tout autre développement de la documentation
  - une autre ligne vide

Exemple d'une fonction documentée sur plusieurs lignes, mais sans format particulier

```{code-cell} python
def racine(a, b, c):
    """Calcul les deux racines d'une équation du second degré.

    L'équation du second degré est de la forme ax² + bx + c = 0.
    La résolution s'appuie sur le calcule du discriminant.
    Note: les solutions peuvent être des nombres complexes

    """
    delta = b**2 - 4 * a * c
    x1 = (-b - delta**0.5) / (2 * a)
    x2 = (-b + delta**0.5) / (2 * a)
    return x1, x2


help(racine)
```

Pour la partie "développement" de la documentation, il existe des formats spécifiques qui facilitent de travail des codeurs et des outils de générateur de documentation en ligne. Les formatages les plus répandus sont
- *Google docstrings* (proposé et recommandé par Google)
- *reStructuredText* (peu lisible, mais très riche)
- [*NumPy/SciPy docstrings*](https://numpydoc.readthedocs.io/en/latest/format.html) (titre le meilleur des deux précédents)

Exemple d'une fonction documentée sur plusieurs lignes avec le format NumPy/SciPy docstrings

```{code-cell}
def racine(a, b, c):
    """Calcul les deux racines d'une équation du second degrés.

    L'équation du second degré est de la forme ax² + bx + c = 0.
    Le discriminant est calculé dans un premier temps, puis
    chacune des deux solutions.

    Parameters
    ----------
    a : int, float
        Coefficient du terme au x².
    b : int, float
        Coefficient du terme x.
    c : int, float
        Coefficient constant

    Returns
    -------
    x1 : real, complex
        Une solution de l'équation.
    x2 : real, complex
        Une solution de l'équation.

    Examples
    --------
    >>> racine(1, -3, 2)
    (1.0, 2.0)

    >>> racine(2, 2, -1.5)
    (-1.5, 0.5)

    >>> racine(2, 2, 1)
    ((-0.5-0.5j), (-0.5+0.5j))

    Notes
    -----
    Les deux solutions renvoyées peuvent être identiques.

    """
    delta = b**2 - 4 * a * c
    x1 = (-b - delta**0.5) / (2 * a)
    x2 = (-b + delta**0.5) / (2 * a)
    return x1, x2


help(racine)
```

