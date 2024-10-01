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

# Classes Python

## Programmation orientée objet

La programmation orientée objet est une façon d'approcher la programmation (paradigme) qui s'appuie sur des "briques logicielles" appelées objets. 

Les **objets** sont un moyen de regrouper 
- des données (**attribut** ou attribut-donnée) et 
- des fonctionnalités (**méthodes** ou attribut-méthode). 

L'**Encapsulation** est le mécanisme qui consiste à regrouper les attributs et les méthodes au sein d'un même objet. L'encapsulation permet également de protéger les données en restreignant l'accès direct à celles-ci et en définissant des méthodes pour les manipuler.

Une **classe** décrit la structure interne des objets et les méthodes qui s'appliqueront aux objets de même famille (même classe). Les objets obtenus à partir d'une classe sont dits **instances** de la classe. 

La figure ci-dessous présente une classe `MaClasse` sous la forme d'un [diagramme de classes](https://fr.wikipedia.org/wiki/Diagramme_de_classes) selon le formalisme [UML](https://fr.wikipedia.org/wiki/UML_(informatique)). Elle définit trois attributs et deux méthodes pour ses instances.

```{mermaid}
classDiagram
    class MaClasse{
        attribut_1
        attribut_2
        attribut_3
        methode_1()
        methode_2()
    }
```

Un objet peut appartenir à plusieurs classes : c'est le **polymorphisme**. Cela permet d'utiliser des objets de classes différentes là où est attendu un objet d'un certain type. Une façon de réaliser le polymorphisme est l'**héritage** de classe, où l'on raffine une classe parente en un autre classe (sous-classe) par des restrictions sur les valeurs possibles des attributs. Ainsi, les objets d'une sous-classe sont conformes à la classe parente. 

Le diagramme de classe UML ci-dessous illustre une classe `Maclasse` qui possède deux parents `Parent_1` et `Parent_2` avec la classe `Parent_2` qui possède elle-même le parent `Parent_3`. Un objet de la classe `Maclasse` hérite de ses classes parentes, cela signifie qu'il à accès aux attributs et aux méthodes de ses parents.

```{mermaid}
classDiagram
    Parent_1 <|-- MaClasse
    Parent_2 <|-- MaClasse
    Parent_3 <|-- Parent_2

    class MaClasse{
        attribut_1
        methode_1()
    }

    class Parent_1{
        attribut_1_1
        methode_1_1()
    }

    class Parent_2{
        attribut_2_1
        methode_2_1()
    }

    class Parent_3{
        attribut_3_1
        methode_3_1()
    }
```


## Exemples du point de vue utilisateur

Les codes suivants instancient des objets de la classe de base `complex` 

```{code-cell} python
complex()  # instancie un objet de classe complex sans argument
```

```{code-cell} python
complex(2, 3)  # instancie un objet de classe complex avec deux arguments
```

La classe `complex` avec ses deux attributs `real` et `imag` et sa méthode `conjugate()` est représentable par le diagramme de classes suivant :

```{mermaid}
classDiagram
    class complex{
        real
        imag
        conjugate()
    }
```

Pour accéder aux attributs ou aux méthodes d'une instance, la notation pointée est utilisée aussi bien pour les attributs que pour les méthodes.

```{code-cell} python
c = complex(2, 3)
c.real  # donne 2.0
```

```{code-cell} python
c.conjugate()  # Appel de la méthode d'instance `conjugate()`
               # Équivalent à complex.conjugate(c)
```

Il faut noter qu'appeler la méthode `conjugate()` depuis l'instance `c` est équivalent à appeler la méthode depuis la classe `complex` avec en 1er argument l'instance sur laquelle appliquer la méthode.

```{code-cell} python
c.conjugate() == complex.conjugate(c)
```

## Définition d'une classe (`class`)

La définition d'une classe se fait avec une instruction composée `class` qui est formée d'une seule clause à la syntaxe suivante :

``` none
class <NomDeClasse> ( <ClassesParentes> ) :
    <suite>
```

où
- `class` est un mot-clé (lexème)
- `<NomDeClasse>` est l'identifiant de la classe définie (lexème), par convention ([PEP 8](https://peps.python.org/pep-0008/#class-names)) on utilise la notation *upper camel case* pour les noms de classes définies par les utilisateurs (ex. : MaClasse, GrapheOriente)
- `<ClassesParentes>` est une suite d'identifiant Python (lexème) qui nomme des classes parentes de `<NomDeClasse>`. Par défaut, si `<ClassesParentes>` ou `( <ClassesParentes> ) ` sont omis, on considère que la suite se limite à la seule classe `object`, la classe parente de toutes les classes.
- `<suite>` est le corps de la classe, il s'agit d'un bloc d'instructions qui doit être non vide et indenté.

La définition d'une classe minimale est

```{code-cell} python
class MaClasse:
    pass
```


## Instanciation d'un objet

La création d'un objet à partir de la classe, l'instanciation, est obtenue avec la syntaxe suivante :

``` none
<NomDeClasse> ( <paramètres> )
```

où
- `<NomDeClasse>` est l'identifiant d'une classe d'objets
- `<paramètres>` est une suite de paramètres utilisés pour initialiser l'objet instancié


Exemples :

```{code-cell} python
MaClasse()  # donne une instance de la classe MaClasse
```

Des attributs d'instances peuvent être ajoutée dans l'espace de non d'une instance avec la notation pointée.

```{code-cell} python
instance_1 = MaClasse()
instance_1.num = 5  # ajout de l'attribut `num` à l'espace de nom de instance_1
instance_1.num
```

Pour vérifier qui `num` est bien un attribut de  `instance_1`, la fonction native `dir()` renvoie la liste des attributs (atrributs-données et attributs-méthodes) valident pour l'instance passée en argument.

```{code-cell} python
dir(instance_1)
```

L'instruction précédente met en évidence de nombreux attributs et méthodes dans l'instance `instance_1` de la classe `MaClasse`. On y voit apparaitre à la fin le nom `num` créé par l'assignation `instance_1.num = 5`

Les identifiants qui commencent par et finissent par deux tirets bas `__` (*double underscore* en anglais) sont des **identifiants spéciaux**, réservés par l'interpréteur Python. Ils sont hérités des classes parentes, ici la classe `object`. Les identifiants spéciaux sont parfois nommés les identifiants dunder (Double UNDERscore).

## Instructions dans la définition d'une classe


Dans le bloc d'instructions `<suite>` de la définition d'une classe, les instructions visent à définir des attributs et des méthodes :

```{list-table} Éléments pouvant être présent dans le bloc &lt;suite> d'une classe
:header-rows: 1

* - Éléments définis
  - Description
  - Instructions utilisées
* - **Méthodes d'instance**
  - Elles sont généralement appelées depuis une instance (notation pointée), dans ce cas l'instance est implicitement envoyée comme premier argument ; par convention le premier paramètre de la définition d'une méthode d'instance qui reçoit cet argument est nommé `self`
  - Instruction composée `def`
* - **Méthodes de classe**
  - Elles sont appelées depuis une classe (notation pointée). L'appel reçoit implicitement la classe en premier argument ; par convention le premier paramètre de la définition d'une méthode de classe  qui reçoit cet argument est nommé `cls`.
  - Instruction d'assignation du retour de la fonction native `classmethod()` appelée avec comme argument, une fonction précédemment définie par l'instruction composée `def`. La syntaxe des décorateurs (sucre syntaxique) `@classmethod` est généralement utilisée.
* - **Méthodes statiques**
  - Elles sont appelées depuis une classe (notation pointée), mais ne reçoivent pas de premier argument implicite contrairement aux méthodes de classe ou aux méthodes d'instance.
  - Instruction d'assignation du retour de la fonction native `staticmethod()` appelée avec comme argument, à une fonction précédemment définie par l'instruction composée `def`. La syntaxe des décorateurs (sucre syntaxique) `@staticmethod` est généralement utilisée.
* - **Attributs de classe**
  - Ils sont partagés par toutes les instances de la classe (dans l'espace de nom de la classe)
  - Instruction d'assignation
* - **Attributs d'instance**
  - Ils sont propres à une instance (dans l'espace de nom d'une instance)
  - Instruction d'assignation du retour de la fonction native `property()`. La fonction `property()` prends comme arguments une fonction "accesseur", une fonction "mutateur" et une fonction "destructeur" de l'attribut d'instance. La syntaxe des décorateurs (sucre syntaxique) est aussi utilisable.<br />  
  Génératement les attributs d'instance sont créés et modifier par des instructions dans les méthodes d'instance.
```

Exemple de définition d'une classe dans laquelle le bloc `<suite>` contient
- la définition de l'attribut de classe `c`
- la définition de la méthode spéciale d'instance `__init__()` (c'est en fait une redéfinition - surcharge - d'une méthode prédéfinie par l'interpréteur Python)
- la définition de la méthode d'instance `accesseur_y()` qui joue le rôle d'accesseur à l'attribut d'instance `y`
- la définition de la méthode d'instance `muatateur_y()` qui joue le rôle de mutateur (modifieur) à l'attribut d'instance `y`
- la définition de l'attribut d'instance `y` à l'aide de la fonction native `property()` et de ses méthodes accesseur et mutateur
- la définition de la méthode de classe `methode_de_classe()` à l'aide de la fonction native `classmethode()` (ici utilisée avec la syntaxe du décorateur `@`, un sucre syntaxique)
- la définition de la méthode statique `methode_de_classe()` à l'aide de la fonction native `classmethod()` (ici utilisée avec la syntaxe du décorateur `@`, un sucre syntaxique) ; une méthode de classe reçoit la classe comme 1er argument
- la définition de la méthode statique `methode_statique()` à l'aide de la fonction native `staticmethod()` (ici utilisée avec la syntaxe du décorateur `@`, un sucre syntaxique) ; une méthode statique ne reçoit reçoit ni l'instance, la classe comme 1er argument

```{code-cell} python
class MaClasse2(object):
    
    c = 123  # attribut de classe
    
    # Méthode spéciale d'instance implicitement appelée 
    # lors de la création d'une nouvelle instance
    def __init__(self):
        """Initialise l'instance."""
        print("------ __init__(self) -------")
        print("self =", self)
        self.x = 0  # attribut d'instance x
        self._y = 0  # attribut d'instance _y semi privé (début "_")
        self.__z = 1  # attribut d'instance __z privé (debut "__")
    
    def methode_d_instance(self, param2):  # méthode d'instance
        """Accède à tous les attributs de l'objet appelant."""
        print("------ methode_d_instance(self, param2) -------")
        print("self =", self)
        print("param2 =", param2)
        u = MaClasse2.c  # accès à l'attribut de classe c (assignation à u)
        v = self.x  # accès à l'attribut d'instance x (assignation à v)
        w = self._y  # accès à l'attribut d'instance _y (assignation à w)
        r = self.__z  # accès à l'attribut d'instance __z (assignation à r)
        MaClasse2.methode_de_classe()  # appel de la méthode de classe
        MaClasse2.methode_statique(34) # appel de la méthode statique
        
    # Méthode d'instance pour accéder à l'attribut d'instance _y
    def accesseur_y(self):
        """renvoie l'attribut d'instance self._y"""
        print("------ accesseur_y(self) -------")
        """Renvoie l'attribut d'instance de _y."""
        return self._y
    
    # Méthode d'instance pour modifier l'attribut d'instance _y
    def muatateur_y(self, valeur):
        """Modifie l'attribut d'instance _y."""
        print("------ muatateur_y(self, val) -------")
        print("self =", self)
        print("val =", valeur)
        self._y = valeur  # assignation de l'attribut d'instance 
        
    # Définition de l'attribut d'instance y à partir de 2 méthodes d'instances
    y = property(accesseur_y, muatateur_y)
    
    # Méthode de classe
    @classmethod
    def methode_de_classe(cls):
        """Affiche la classe appelante et son attribut de classe c."""
        print("------ methode_de_classe(cls) -------")
        print("cls =", cls)
        print("attribut de classe =", cls.c)
    
    # Méthode statique
    @staticmethod
    def methode_statique(param1):
        """Affiche le paramètre associé au seul argument reçu."""
        print("------ methode_statique(param1) -------")
        print("ne reçoit pas d'argument implicite")
        print("param1 =", param1)
```

Exemples d'utilisation de la classe `MaClasse2` définie ci-dessus :

- Création d'une instance de MaClasse2, ce qui génère un appel implicite de la méthode `__init__()`

```{code-cell} python
a = MaClasse2()
```

- Assignation de la valeur 2 à l'attribut `x` de l'instance `a`

```{code-cell} python
a.x = 2
```

- Assignation de la valeur 3 à l'attribut `y` de l'instance `a`

```{code-cell} python
a.y = 3
```

- Accès interdit à l'attribut privé `__z` de l'instance `a`

```{code-cell} python
a.__z
```

- Appel de la méthode d'instance `methode_d_instance()` depuis l'instance `a`

```{code-cell} python
a.methode_d_instance(92)
```

- Appel de la méthode de classe `methode_de_classe()` depuis la classe  `MaClasse2`

```{code-cell} python
MaClasse2.methode_de_classe()
```

- Appel de la méthode statique `methode_statique()` depuis la classe  `MaClasse2`

```{code-cell} python
MaClasse2.methode_statique(64)
```

## Méthodes spéciales

En Python, les méthodes spéciales sont des méthodes prédéfinies qui commencent et se terminent par deux tirets bas `__` (*underscore* en anglais) ; elles sont aussi appelées "dunder methods" pour "Double UNDERscore methods". Elles permettent de définir le comportement des objets pour certaines opérations et interactions. Dans la pratique, le langage Python et ses fonctions natives utilisent ces méthodes spéciales pour réaliser des opérations de base sur le objets, comme l'affiche textuel, les comparaisions entre objet, les opération arithmétique entre objet, les opération d'itération ... Les méthodes spéciales sont donc essentielles pour créer des classes personnalisées qui s'intègrent bien avec les fonctionnalités du langage Python.

Voici une liste des méthodes spéciales les plus courantes :

### Méthodes Spéciales de Base

- `__init__(self, ...)` : Initialise une instance, appelé automatiquement lors de la création d'une nouvelle instance.
- `__del__(self)` : Destructeur d'instance', appelé lors de la destruction d'une instance.
- `__repr__(self)` : Représentation officielle de l'objet, utilisée par la fonction native `repr()`, elle-même utilisée pour représenter les objets dans la partie interactive de l'interpréteur Python.
- `__str__(self)` : Représentation informelle de l'objet, utilisée par le constructeur d'instance `str()`, elle-même utilisée par `print()`.
- `__bytes__(self)` : Représentation de l'instance en bytes, utilisée par le constructeur d'instance `bytes()`.
- `__format__(self, format_spec)` : Formatage de l'instance, utilisée par la fonction native`format()`.

### Méthodes Spéciales pour les comparaisons

- `__lt__(self, autre)` : Renvoie `True` si l'instance est inféreure à `autre`, sinon `False` ; méthode utilisée par l'opérateur inférieur à `<`.
- `__le__(self, autre)` : Renvoie `True` si l'instance est inféreure ou égale à `autre`, sinon `False` ; méthode utilisée par l'opérateur inférieur ou égale à `<=`.
- `__eq__(self, autre)` : Renvoie `True` si l'instance est égale à `autre`, sinon `False` ; méthode utilisée par l'opérateur égal à `==`.
- `__ne__(self, autre)` : Renvoie `True` si l'instance est différent de `autre`, sinon `False` ; méthode utilisée par l'opérateur différent de `!=`.
- `__gt__(self, autre)` : Renvoie `True` si l'instance est supérieure à `autre`, sinon `False` ; méthode utilisée par l'opérateur supérieur à `>`.
- `__ge__(self, autre)` : Renvoie `True` si l'instance est supérieure ou égale à `autre`, sinon `False` ; méthode utilisée par l'opérateur supérieur ou égal à `>=`.

### Méthodes Spéciales pour les opérations arithmétiques

- `__add__(self, autre)` : Renvoie la résultat de l'expression de `self + autre`.
- `__sub__(self, autre)` : Renvoie la résultat de l'expression de `self - autre`.
- `__mul__(self, autre)` : Renvoie la résultat de l'expression de `self * autre`.
- `__truediv__(self, autre)` : Renvoie la résultat de l'expression de `self / autre`.
- `__floordiv__(self, autre)` : Renvoie la résultat de l'expression de `self // autre`.
- `__mod__(self, autre)` : Renvoie la résultat de l'expression de `self % autre`.
- `__pow__(self, autre)` : Renvoie la résultat de l'expression de `self ** autre`.
- `__and__(self, autre)` : Renvoie la résultat de l'expression de `self & autre`.
- `__or__(self, autre)` : Renvoie la résultat de l'expression de `self | autre`.
- `__xor__(self, autre)` : Renvoie la résultat de l'expression de `self ^ autre`.
- `__lshift__(self, autre)` : Renvoie la résultat de l'expression de `self << autre`.
- `__rshift__(self, autre)` : Renvoie la résultat de l'expression de `self >> autre`.

### Méthodes spéciales pour les opérations unaires

- `__neg__(self)` : Renvoie la résultat de l'expression de `- self`.
- `__pos__(self)` : Renvoie la résultat de l'expression de `+ self`.
- `__abs__(self)` : Renvoie la résultat de l'expression de `abs(self)`.
- `__invert__(self)` : Renvoie la résultat de l'expression de `~ self`.

### Méthodes spéciales pour les conteneurs

- `__len__(self)` : Renvoie la résultat de l'expression de `len(self)`.
- `__getitem__(self, key)` : Accès à un élément, utilisée par `self[key]`.
- `__setitem__(self, key, value)` : Assignation d'un élément, utilisée par `self[key] = value`.
- `__delitem__(self, key)` : Suppression d'un élément, utilisée par `del self[key]`.
- `__iter__(self)` : Retourne un itérateur, utilisée par `iter(self)`.
- `__next__(self)` : Retourne l'élément suivant, utilisée par `next(self)`.
- `__contains__(self, item)` : Vérifie la présence d'un élément, utilisée par `in`.

### Exemple d'Utilisation

Voici un exemple de classe utilisant certaines de ces méthodes spéciales :

```{code-block} python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return f"Point({self.x}, {self.y})"

    def __str__(self):
        return f"({self.x}, {self.y})"

    def __add__(self, other):
        if isinstance(other, Point):
            return Point(self.x + other.x, self.y + other.y)
        return NotImplemented

    def __eq__(self, other):
        if isinstance(other, Point):
            return self.x == other.x and self.y == other.y
        return NotImplemented

    def __len__(self):
        return int((self.x**2 + self.y**2)**0.5)

# Utilisation de la classe Point
p1 = Point(1, 2)
p2 = Point(3, 4)
print(p1)  # Affiche (1, 2)
print(repr(p1))  # Affiche Point(1, 2)
print(p1 + p2)  # Affiche (4, 6)
print(p1 == p2)  # Affiche False
print(len(p1))  # Affiche 2
```