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

```{note}
En construction
```

# Classes Python

## Programmation orientée objet

La programmation orientée objet est une façon d'approcher la programmation (paradigme) qui s'appuie sur des "briques logicielles" appelées objets. 

Les **objets** sont un moyen de regrouper 
- des données (**attribut** ou attribut-donnée) et 
- des fonctionnalités (**méthodes** ou attribut-méthode). 

L'**Encapsulation** est le mécanisme qui consiste à regrouper les attributs et les méthodes au sein d'un même objet. L'encapsulation permet également de protéger les données en restreignant l'accès direct à celles-ci et en définissant des méthodes pour les manipuler.

Une **classe** décrit la structure interne des objets et les méthodes qui s'appliqueront aux objets de même famille (même classe). Les objets obtenus à partir d'une classe sont dits **instances** de la classe. 

La figure ci-dessous présente une classe `MaClasse` sous la forme d'un [diagramme de classes](https://fr.wikipedia.org/wiki/Diagramme_de_classes) selon le formalisme [UML](https://fr.wikipedia.org/wiki/UML_(informatique)). Elle définie trois attributs et deux méthodes pour ses instances.

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

Le diagramme de classe UML ci-dessous illustre une classe `Maclasse` qui possède deux parents `Parent_1` et `Parent_2` avec la classe `Parent_2` qui possède elle-même le parents `Parent_3`. Un objet de la classe `Maclasse` hérite de ses classes parentes, cela signifie qu'il à accès aux attributs et aux méthodes de ses parrents.

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

Pour accéder aux attributs ou aux méthodes d'une instance, la notation pointé est utilisée aussi bien pour les attributs que pour les méthodes.

```{code-cell} python
c = complex(2, 3)
c.real  # donne 2.0
```

```{code-cell} python
c.conjugate()  # Appel de la méthode d'instance `conjugate()`
               # Equivalent à complex.conjugate(c)
```

Il faut noter qu'appeller la méthode `conjugate()` depuis l'instance `c` est équivalent à appeller la méthode depuis la classe `complex` avec en 1er argument l'instance sur laquelle appliquer la méthode.

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
- `<NomDeClasse>` est l'identifiant de la classe définie (lexème), par convention ([PEP 8](https://peps.python.org/pep-0008/#class-names)) on utilise la notation *upper camel case* pour les noms de classes définies par les utilisateurs (ex : MaClasse, GrapheOriente)
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

L'instruction précédente met en évidence de nombreux attributs et méthodes dans l'instance `instance_1` de la classe `MaClasse`. On y voit apparaitre à la fin le nom `num` crée par l'assignation `instance_1.num = 5`

Les identifiants qui commencent par et finissent par deux tirets-bas `__` (*double underscore* en anglais) sont des **identifants spéciaux**, réservés par l'interpréteur Python. Ils sont hérités des classes parentes, ici la classe `object`. Les identifiants spéciaux sont parfois nommés les identifiants dunder (Double UNDERscore).

## Instructions dans la définition d'une classe


Dans le bloc d'instructions `<suite>` de la définition d'une classe, les instructions visent à définir des attributs et des méthodes :

```{list-table} Eléments pouvant être présent dans le bloc &lt;suite> d'une classe
:header-rows: 1

* - Eléments défini
  - Description
  - Instructions utilisées
* - **Méthodes d'instance**
  - Elles sont généralement appelées depuis une instance (notation pointée), dans ce cas l'instance est implicitement envoyée comme premier argument ; par convention le premier paramètre de la définition d'une méthode d'instance qui reçoit cet argument est nommé `self`
  - Instruction composée `def`
* - **Méthodes de classe**
  - Elles sont appelées depuis une classe (notation pointée). L'appel reçoit implicitement la classe en premier argument ; par convention le premier paramètre de la définition d'une méthode de classe  qui reçoit cet argument est nommé `cls`.
  - Instruction d'assignation du retour de la fonction native `classmethod()` appelée avec comme argument, une fonction précédemment définie par l'instruction composée `def`. La syntaxe des décorateurs (sucre syntaxique) `@classmethod` est généralement utilisée.
* - **Méthodes statique**
  - Elles sont appelées depuis une classe (notation pointée), mais ne reçoivent pas de premier argument implicite contrairement aux méthodes de classe ou aux méthodes d'instance.
  - Instruction d'assignation du retour de la fonction native `staticmethod()` appelée avec comme argument, à une fonction précédemment définie par l'instruction composée `def`. La syntaxe des décorateurs (sucre syntaxique) `@staticmethod` est généralement utilisée.
* - **Attributs de classe**
  - Ils sont partagés par toutes les instances de la classe (dans l'espace de nom de la classe)
  - Instruction d'assignation
* - **Attributs d'instance**
  - Ils sont propre à une instance (dans l'espace de nom d'une instance)
  - Instruction d'assignation du retour de la fonction native `property()`. La fonction `property()` prend comme arguments une fonction "assesseur", une fonction "mutateur" et une fonction "destructeur" de l'attribut d'instance. La syntaxe des décorateurs (sucre syntaxique) est aussi utilisable.<br />  
  Génératement les attributs d'instance sont créer et modifier par des instruction dans les méthodes d'instance.
```

Exemple de définition d'une fonction dans laquelle le bloc `<suite>` contient
- la définition de l'attribut de classe `c`
- la définition de la méthode spéciale d'instance `__init__()` (c'est en fait une redéfinition - surcharge - d'une méthode prédéfinie par l'interpréteur Python)
- la définition de la méthode d'instance `methode_d_instance()`
- la définition de la méthode d'instance `methode_d_instance()`
- la définition de la méthode d'instance `methode_d_instance()`
- la définition 

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
    
    def methode_d_instance(self, param2):  # methode d'instance
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
    def assesseur_y(self):
        """renvoie l'attribut d'instance self._y"""
        print("------ assesseur_y(self) -------")
        """Renvoie l'attribut d'instance de _y."""
        return self._y
    
    # Méthode d'instance pour modifier l'attribut d'instance _y
    def muatateur_y(self, valeur):
        """Modifie l'attribut d'instance _y."""
        print("------ muatateur_y(self, val) -------")
        print("self =", self)
        print("val =", valeur)
        self._y = valeur  # assignation de l'attribut d'instance 
        
    # Définition de l'attribut d'instance y à parir de 2 méthodes d'instances
    y = property(assesseur_y, muatateur_y)
    
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

Création d'une instance de MaClasse2, ce qui génére un appel implicite de la méthode `__init__()`

```{code-cell} python
a = MaClasse2()
```

Assignation de la valeur 2 à l'attribut `x` de l'instance `a`

```{code-cell} python
a.x = 2
```

Assignation de la valeur 3 à l'attribut `y` de l'instance `a`

```{code-cell} python
a.y = 3
```

Accès interdit à l'attribut privé `__z` de l'instance `a`

```{code-cell} python
a.__z
```

Appel de la méthode d'instance `methode_d_instance()` depuis l'instance `a`

```{code-cell} python
a.methode_d_instance(92)
```

Appel de la méthode de classe `methode_de_classe()` depuis la classe  `MaClasse2`

```{code-cell} python
MaClasse.methode_de_classe()
```

Appel de la méthode statique `methode_statique()` depuis la classe  `MaClasse2`

```{code-cell} python
MaClasse2.methode_statique(64)
```





```{code-cell} python
:linenos:
class MaClasse2:

    def methode(self, parametre_2):
        """Méthode d'instance."""
        x = 3  # "variable classique" (locale à la méthode)
        self.x = parametre_2  # attribut de l'instance (local à l'objet)
        print("Ceci est une méthode d'instance")
```

- La ligne 1 est l'entête de l'unique clause de la déclaration d'une classe
- La ligne 3 est le début de l'instruction composée `def` qui définit une méthode d'instance. Les deux paramètres de la définition de la méthode sont respectivement, le paramètre qui reçois l'instance passer implicitement en argument à l'appel depuis l'instance (nommée par convesion `self`) puis le paramètre `parametre_2`
- La ligne 5 définie le nom `x`, un nom local à la fonction (méthode) qui disparaitra à la fin de l'exécution de la méthode. 
- - La ligne 6 définie le nom `x` dans l'espace de nom de l'instance avec la notation pointés `self.x`, ce nom persistera au delà de l'exécution de la méthode dans l'instance. C'est l'objet reçu dans le paramètre `parametre_2` est assigné à `self.x`.

L'appelle à une méthode d'instance se fait depuis une instance par la notation pointée. Exemple

```{code-cell} python
instance = MaClasse2()  # instanciation d'un objet de type MaClasse
instance.methode(-34)  # appelle de la méthode d'instance `.methode()`
instance.x  # donne -34, la valeur de l'attribut x
```

Les autres instructions qui l'on trouve dans `<suite>`  définissent :
- les **attributs de classe** qui sont partagés par toutes les instances de la classe (dans l'espace de nom de la classe)
- les **attributs d'instance** qui sont propre à une instance (dans l'espace de nom d'une instance)
- les **méthodes de classe** qui sont appelées depuis une classe et qui reçoivent implicitement la classe en premier argument ; par convention le premier paramètre de la définition d'une méthode de classe est nommé `cls`.
- les **méthodes statiques** qui sont appelées depuis une instance, mais qui ne reçoivent pas de premier argument implicitement contrairement aux méthodes de classe ou aux méthodes d'instance.


###