# Glossaire Python

## A

````{glossary}
Argument
    Objet Python fourni au moment de l'appel à une fonction ou à une méthode.
    L'argument peut ête positionnel ou nommé.

Argument nommée
    Un argument précédé d'un identifiant (comme `name=`) ou un dictionnaire précédé de `**`, lors d'un appel de fonction où de méthode. Par exemple, '3' et '5' sont tous les deux des arguments nommés dans l'appel à complex() ici :

    ```python
    complex(real=3, imag=5)
    args = {'real': 3, 'imag': 5}
    complex(**args)
    ```
````

## B

```{glossary}
Bytecode
    voir Code intermédiaire
```

## C

```{glossary}
Cadre d'exécution

Code intermédiare (bytecode)

Complexité temporelle
    https://wiki.python.org/moin/TimeComplexity

    https://wiki.python.org/moin/PythonSpeed?highlight=%28CategoryDocumentation%29

    https://www.linkedin.com/pulse/demystifying-python-data-structure-time-space-complexity-deepak-s/

    https://ics.uci.edu/~pattis/ICS-33/lectures/complexitypython.txt

    https://nsikakimoh.com/blog/time-complexities-of-python-data-type

    https://www.tutorialspoint.com/complexity-cheat-sheet-for-python-operations

    https://copyprogramming.com/howto/how-to-find-out-time-complexity-of-python-function
```

## E

```{glossary}
Espace de nommage
    L'endroit où le nom des objets Python sont stockée. 

Espace des objets
    ...
```

## H

```{glossary}
Hachable
    Un objet Python est hachable s'il possède une valeur de hachage qui ne change jamais au cours de sa vie (il a besoin d'une méthode `__hash__()`) et peut être comparé aux d'autres objets de sa classe (il a besoin d'une méthode `__eq__()`). Les objets hachables qui se comparent de manière égale doivent avoir la même valeur de hachage.

    La hachabilité permet à un objet d'être utilisé comme clé de dictionnaire ou en tant que membre d'un ensemble (type set), car ces structures de données utilisent cete valeur hashage.

    La plupart des types [immuables](content:memento:immuable) natifs de Python sont hachables, mais les conteneurs {term}`muable`s (comme les listes ou les dictionnaires) ne le sont pas ; les conteneurs {term}`immuable`s (comme les n-uplets ou les ensembles figés) ne sont hachables que si leurs éléments sont hachables. Les instances de classes définies par les utilisateurs sont hachables par défaut. Elles sont toutes considérées différentes (sauf avec elles-mêmes) et leur valeur de hachage est calculée à partir de leur `id()`.
```
## I

```{glossary}
(content:memento:immuable)=
Immuable
    Objet Python dont la valeur ne change jamais. Les nombres, les chaînes et les n-uplets sont immuables. Ils ne peuvent être modifiés. Un nouvel objet doit être créé si une valeur différente doit être stockée. Ils jouent un rôle important quand une valeur de hashache constante est requise, typiquement en clé de dictionnaire.
```

## L

```{glossary}
Liste
    Type d'objet natif de sequence dans Python. En dépit de son nom, une liste ressemble plus à un tableau (*array* dans la plupart des langages) qu'à une liste chaînée puisque les accès se font en O(1).
```
## M

```{glossary}
Machine virtuel Python
    La machine virtuelle Python est conçue pour exécuter les codes intermédiaires (bytecodes) dans un environnement indépendant de la plate-forme matérielle (Système d'explotation et processeur).

Méthode (de classe, d'objet)
    Fonction définie à l'intérieur d'une classe. Lorsqu'elle est appelée comme un attribut d'une instance de cette classe, la méthode reçoit l'instance en premier argument positionel (qui, par convention, est habituellement nommé `self`)

Muable
    Objet Python dont la valeur peut changer tout en conservant le même `id()`.
```

## N

```{glossary}
n-uplet

n-uplet nommé
```

## O

```{glossary}
Objet Python
    N'importe quelle donnée comportant des états (sous forme d'attributs ou d'une valeur) et un comportement (des méthodes). Un entier, une liste, un dictionnaire ou une instance d'une classe définie par le développer sont des exemples d'objets Python. 

    Chaque objet Python a un `id()` unique et un compteur de références `sys.getrefcount()` qui indique le nombre de noms dans l'espace de nommage qui le réfère. Lorsque son compteur de références descend à zéro l'objet est désalloué et le ramasse-miettes 
```

## P
```{glossary}
Paramètre

PEP (Python Enhancement Proposal)
    Une PEP, proposition d'amélioration de Python, est un document de conception fournissant des informations à la communauté Python ou décrivant une nouvelle fonctionnalité pour Python, ses processus ou son environnement. Les PEP doivent fournir une spécification technique concise et une justification des fonctionnalités proposées.

    Les PEP sont censées être les principaux mécanismes pour proposer de nouvelles fonctionnalités majeures, pour recueillir les commentaires de la communauté sur une question et pour documenter les décisions de conception qui sont intégrées en Python. L’auteur du PEP est responsable de l’établissement d’un consensus au sein de la communauté et de documenter les opinions contradictoires.
```

## R

```{glossary}
(content:memento:garbage_collection)=
ramasse-miettes (garbage collection)
    Le rammasse-miettes est mécanisme permettant de libérer de la mémoire lorsqu'elle n'est plus utilisée durant l'exécution d'un programme Python. Lorsqu'un objet Python est désalloué par la commande native `del` ou par la cloture d'un cadre d'exécution (fin d'exécution d'une fonction) et que le compteur de référence de cet object arrive à zéro, le rammasse-miettes à pour fonction de libérer la mémoire qu'il occupait pour la rendre diponible pour de nouveaux objets Python que le programme aura besoin de créer.

    Le rammasse-miettes est automatiquement gérer par l'interpréteur Python. Cependant, si le développeur en à besoin, il est possible d'en contrôler le fonctionnement depuis la programme à l'aide du modude standard `gc` (Garbage Collector interface)
```

## S

```{glossary}
Sources 
    - https://docs.python.org/fr/3/glossary.html#term-generator
```

## T

```{glossary}
Tranche (slice)
    Une tranche est un objet Python qui représente un ensemble d'indices spécifié par un début, une fin et un pas de progression. Lorsque l'on applique un objet tranche à un object de type séquences comme une liste ou un chaîne, une nouvelle séquence est renvoyée contenant uniquement les éléments de la séquence originale incidés par l'objet tranche ; on appelle cela une opération de tranchage (*slicing* en anglais).

    Une tranche allant de l'indice 2 à l'incide 11 exclu avec un pas de 3 s'écrit `slice(2, 11, 3)` ; elle décrit l'ensemble des indices 2, 5, 8. Si `ma_liste` est une séquence de type liste de longueur supérieur à 11, alors `ma_liste[slice(2, 11, 3)]` est une nouvelle liste egale à `[ma_liste[2], ma_liste[5], ma_liste[8]]`. Le même tranchage peut s'exprimé avec une notation plus compacte `ma_liste[2:11:3]`.

Type
    Le type d'un objet Python détermine le genre d'objet qu'il est comme par exemple un entier, un réel, une chaîne, une liste ou un dictionnaire. Tous les objets ont un type. Le type d'un objet peut être obtenu via son attribut `__class__` ou via la fonction native `type()`.
```
