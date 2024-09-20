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

# Langage Python

## Grammaire

La syntaxe d'un code source en langage Python est définie par une **grammaire formelle** (disponible ici : https://docs.python.org/fr/3/reference/grammar.html). Elle spécifie comment un axiome et des symboles non terminaux sont construits à partir de symboles terminaux et de règles de productions. Concrètement,
- **l'axiome** représente l'ensemble des codes source Python possible
- **les symboles terminaux** sont des éléments lexicaux de base (lexèmes) comme des mots-clés, des nombres, des identifiants, des opérateurs...
- **les règles de production** décrivent les assemblages possibles de lexèmes en nouveaux éléments intermédiaires (les symboles non terminaux) et elles décrivent aussi les assemblages des symboles non terminaux entre eux pour construire l'axiome (les codes source possibles)

Pour interpréter un code source, il faut commencer par une **analyse lexicale** qui identifie les lexèmes et qui accessoirement élimine les commentaires et les lignes vides, puis continuer par une **analyse syntaxique** en s'appuyant sur les de production de la grammaire (règle de syntaxe) pour identifier les instructions et leur structure.

## Commentaires

Les commentaires en Python commencent avec un caractère croisillon, #, et s'étendent jusqu'à la fin de la ligne. Un commentaire peut apparaitre dès le début d'une ligne ou après un ou plusieurs espaces, ou à la suite d'un fragment de code, mais pas à l'intérieur d'une chaine de caractères littérale. Un caractère croisillon à l'intérieur d'une chaine de caractères est juste un caractère croisillon. Exemples :

``` python
# Ce commentaire occupe toute la ligne
     # Ce commentaire débute après quelques espaces
a = 123  # Ce commentaire fait suite au fragment de code "a = 123"
s = "Suivez le hashtag #python"  # le 1er # fait parti d'une chaine
```

La grammaire formelle qui décrit la syntaxe du langage n'intègre pas les commentaires. Ils sont donc tout simplement éliminés par l'interpréteur Python avant de lire les instructions. 

Les principales utilisations des commentaires sont :

- planifier les futures nouvelles parties de votre code. Ne pas oublier pas de supprimer ces commentaires une fois que le code est écrit.

``` python
# Ici, je dois ajouter une vérification que l'entier saisi est positif
```

- décrire le code en expliquant l'intention de sections de code spécifiques

``` python
# Tenter une connexion avec des paramètres précédents. 
# En cas d'échec, l'utilisateur est invité à changer les paramètres.
```

- décrire un choix d'algorithmique (pourquoi un algorithme spécifique est-il sélectionné ?) ou son principe de fonctionnement

``` python
# L'algorithme A* à préféré à Dijkstra car une estimation du
# meilleur chemin est possible et les performances sont accrues.
```

- étiqueter des sections de code spécifiques où se trouvent des problèmes identifiés ou des axes d'amélioration. On peut citer à titre d'exemple les étiquettes BUG, FIXME, et TODO souvent écrites est anglais pour les compacités.

``` python
# TODO: Ajouter une condition

# BUG: une division par 0 se produit alors que le dénominateur
#      est censé être toujours supérieur à 1
```

## Lexèmes

Les lexèmes (*tokens* en anglais) sont des symboles lexicaux comme `+`, `-`, `(`, `)`, `for`, `if`, `23`, `"Bonjour"` qui représentent des symboles élémentaires (symboles terminaux) pour la grammaire du langage. Ils se répartissent en différentes catégories selon leur signification : les **identifiants** d'objet, les **mots-clés** réservés, les **littéraux** d'objet, les **opérateurs** comme l'addition ou la division et les **délimiteurs** comme `;` `(` ou `)` pour séparer ou regrouper des éléments.



::::{grid}
:gutter: 2

:::{grid-item-card} Identifiants
Symboles représentant des noms d'objet, de fonctions, de classes, de modules... Ils sont composés de lettres, de chiffres (sauf pour le 1er caractère), et de tirets bas `_`. Exemples : 

```none
x    angle_min     capteur_12
n    mon_adresse   matrice_3x3
i    vitesse_x     _12e_point`
```
:::

:::{grid-item-card} Mots-clés

Mots réservés par le langage pour construire les instructions

``` none
False     class     from      or
None      continue  global    pass         
True      def       if        raise         
and       del       import    return     
as        elif      in        try   
assert    else      is        while        
async     except    lambda    with         
await     finally   nonlocal  yield
break     for       not   
```
:::

::::

::::{grid}
:gutter: 2

:::{grid-item-card} Mots-clés ad hoc

Mots réservés dans le contexte de l'instruction "match" (depuis la version 3.10)

``` none
match     case      _    
```
Mots réservés dans le contexte de l'instruction "type" (depuis la version 3.12)

``` none
type
```
:::

:::{grid-item-card} Littéraux
Symboles pour indiquer des valeurs de nombres (entier, flottant, imaginaire, booléen), de chaines de caractères. Exemples : 

```none
121       742900      30097246882642
12.2      8.54e-6     -12.76e102
5j        2 + 1j      6.2 - 9.5j
True      False       None
'Newtow'  "N. Tesla"  "Le Corbusier"  
```

:::


::::

::::{grid}
:gutter: 2

:::{grid-item-card} Opérateurs
Symboles qui opèrent sur des opérandes et qui produisent un résultat, comme l'addition, la multiplication 

```
+       -       *       **
/       //      %       @
<<      >>      &       |
^       ~       :=
<       >       <=      >=
==      !=
```
:::

:::{grid-item-card} Délimiteurs

Symboles qui regroupent les éléments d'une instruction, sauf `;` qui sépare les instructions.

```
(       )       [       ]       {
}       ,       :       !       .
.       ;       @       =       ->
+=      -=      *=      /=      //=
%=      @=      &=      |=      ^=
>>=    <<=     **=
```
:::

::::

::::{grid}
:gutter: 2

:::{grid-item-card} Symboles de contrôle

```
NEWLINE     INDENT      DEDENT     ENDMARKER
```

Lexèmes qui traduisent certains caractères de contrôle de la position du prochain caractère dans le code source. NEWLINE est le symbole qui indique qu'une fin de ligne logique est présente, les symboles INDENT et DEDENT traduisent une indentation ou une désindentation de la ligne logique par rapport au précédent niveau d'indentation, et le symbole ENDMARKER indique la fin du code source. 
:::

::::

**Les fins de ligne : lexème `NEWLINE`**

Python fait la différence entre une ligne physique, c'est-à-dire une ligne de texte dans le code source, et une ligne logique. L'idée est de pouvoir écrire des instructions très longues sans les écrire sur des lignes de texte trop longues pour en faciliter la lisibilité.  Dans la proposition d'amélioration de Python [PEP 8](https://peps.python.org/pep-0008/#maximum-line-length), il est recommandé de limiter la longueur des lignes du code source à 79 caractères, et même à 72 caractères pour les commentaires et les chaines de documentation "docstrings".

Deux lignes physiques, ou plus, peuvent être jointes pour former une seule ligne logique en utilisant la barre oblique inversée `\` (sauf dans un commentaire ou dans un lexème littéral de type chaine de caractères). Les commentaires après la barre oblique inversée sont interdits. Exemple d'une ligne logique écrite sur 3 lignes physiques :

``` python
calcul = 12.1457 \
    + 76.7 ** 3 \
    - 5.6 * 0.265  # formule longue
```

L'analyse lexicale des lignes physiques précédentes donne la suite de lexèmes suivante :

`calcul` `=` `12.1457` `+` `76.7` `**` `3` `-` `5.6` `*` `0.265` `ENDMARKER` 

Les caractères barre oblique `\` et le commentaire de ne génèrent pas de lexème.

Les expressions entre parenthèses, crochets ou accolades peuvent être réparties sur plusieurs lignes sans utiliser de barre oblique inversée. Dans ce cas, un commentaire est possible à la fin de chaque ligne physique. Par exemple :


``` python
calcul = (12.1457   # 1re ligne physique de la ligne logique
    + 76.7 ** 3     # 2e ligne physique de la ligne logique
    - 5.6 * 0.265)  # dernière ligne physique de la ligne logique
```

L'analyse lexicale des lignes physiques précédentes donne la suite de lexèmes suivante :

`calcul` `=` `(` `12.1457` `+` `76.7` `**` `3` `-` `5.6` `*` `0.265` `)` `ENDMARKER`

Ici les parenthèses sont prises en compte, des lexèmes sont générés et ils seront traités par les règles de grammaire qui décrivent la syntaxe.

Les lignes physiques "vide" contenant uniquement des espaces et des tabulations sont ignorées (elles ne génèrent pas de lexèmes).

**L'indentation : lexèmes `INDET` et `DEDENT`**

Des espaces au début d’une ligne logique sont utilisés pour connaitre le niveau d’indentation de la ligne, qui est ensuite utilisé pour déterminer comment les instructions sont groupées en blocs (des suites d'instructions dans les clauses d'instructions composées). Dans le code source suivant, les lignes logiques se placent à deux niveaux d'indentation en plus du niveau de base.

```python
n = 4  # initialisation de n
print("-- début --")
for i in range(n):
    print("i =", i)
    if i % 2 == 0:  # test si i est pair
        print("i est pair")
    print("---")  # séparateur d'itération
print("-- fin --")
```

L'analyse lexicale de ce code source donne une suite lexèmes où apparaissent `IDENT` et `DEDENT`. Le résultat d'analyse est présenté ci-dessous. Pour la lisibilité les fins de ligne physique du code source ont été concernées.

`n` `=` `4` **`NEWLINE`**<br />
`print` `(` `"-- début --"` `)` **`NEWLINE`**<br />
`for` `i` `in` `range` `(` `n` `)` `:` **`NEWLINE`**<br />
&nbsp;&nbsp;&nbsp;&nbsp;**`IDENT`** `print` `(` `"i ="` `,`  `i` `)` **`NEWLINE`**<br />
&nbsp;&nbsp;&nbsp;&nbsp;`if` `i` `%` `2` `==` `0` `:`  **`NEWLINE`**<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**`IDENT`** `print` `(` `"i est pair"` `)` **`NEWLINE`**<br />
&nbsp;&nbsp;&nbsp;&nbsp;**`DEDENT`** `print` `(` `"---"` `)` **`NEWLINE`**<br />
**`DEDENT`** `print` `(` `"-- fin --"` `)` `ENDMARKER`<br />

Les lexèmes identifiés sont :
- les identifiants `n`, `i`, `print` et `range`
- les mots-clés `for`, `in` et `if`
- les littéraux `4`, `"-- début --"`, `"i ="`, `2`, `0`, `"i est pair"`, `---` et `"-- fin --"`
- les opérateurs `%`, et `==`
- les délimiteurs `=`, `(`, `)` et `:`
- les symboles de contrôle `NEWLINE`, `IDENT`, `DEDENT` et `ENDMARKER`

## Objets Python

Avec Python toutes les données sont représentées sous forme d’objets. Un objet est une entité stockée dans la mémoire de la machine hôte, qui possède :
- une **valeur** - On dit que les objets `a` et `b` possèdent la même valeur si l'évaluation de l'expression de comparaison `a == b` retourne `True` (ou plus exactement un objet de type booléen et de valeur égale à `True`). Python ne dispose pas de méthode canonique pour accéder à la valeur d'un objet.
- un **type** - Chaque objet est l'instance d'une *classe* que l'on appelle aussi le type de l'objet. Un objet conserve toujours le même type au cours de son existence en mémoire, on parle de typage fort du langage Python. La fonction native `type()` retourne le type (la classe) de l'objet passé en argument. On dit que les objets `a` et `b` possèdent le même type si l'évaluation de l'expression `type(a) == type(b)` retourne `True`
- une **identité** - Chaque objet possède une identité unique qui ne change jamais au cours de son existence en mémoire, on parle d'identifiant. La fonction native `id()` retourne l'identifiant de l'objet passé en argument. On dit que les objets `a` et `b` ont la même identité s'ils ne font qu'un, c'est-à-dire si l'évaluation de l'expression `id(a) == id(b)` retourne `True`, c'est-à-dire si l'évaluation de l'expression `a is b` retourne `True`.
- des **attributs-données**, éventuellement aucun - Les attributs-données, parfois simplement nommés attributs, sont des données de n'importe quel type qui caractérisent l'objet. Elle sont dites encapsulées dans l'objet. Pour désigner un attribut nommé `nom_attr` de l'objet `obj` il y a deux possibilités : 
  - la notation "pointée" `obj.nom_attr`
  - la fonction native `getattr(obj, nom_attr)` 
- des **attributs-méthodes**, éventuellement aucun - Les attributs-méthodes, parfois simplement nommées méthodes, sont utiles pour définir des comportements spécifiques à l'objet, permettant ainsi une grande flexibilité et encapsulation des données. Ce sont des fonctions encapsulées qui s'appliquent à l'objet qui la possède. Pour appeler la méthode `meth()` de l'objet `obj`, il est également possible d'utiliser la notation pointée : `obj.meth()` avec éventuellement des arguments à transmettre entre les parenthèses.
La figure suivante illustre graphiquement la notion d’objet Python. À droite, une version détaillée qui montre tout ce qui est encapsulé dans l’objet (sa valeur, son type, son identité, ses attributs-données et ses attributs-méthodes) et à gauche une représentation compacte avec juste son type et sa valeur.

```{figure} img/objet_01.png
---
width: 300px
align: center
---
Représentations graphiques d'un objet Python<br />version détaillée (à gauche), version compacte (à droite)
```

### Types d'objet

Chaque objet est l’instance d’une classe que l’on appelle aussi le type de l’objet. Un objet conserve toujours le même type au cours de son existence en mémoire, on parle de typage fort. Le langage Python propose des types natifs de données que l'on peut présenter en quatre grandes familles :

- les **types de base** comme les nombres et le type "vide"

``` python
12  # un nombre entier
1.34  # un nombre à virgule flottante
2 + 3j  # un nombre complexe ou j est le nombre imaginaire
True  # le nombre booléen vrai
False  # le nombre booléen faux
None  # l'objet "vide"
```

- les **types conteneur** qui contiennent une collection d’éléments comme les chaines de caractères, les listes d'objets, les ensembles d'objets, les associations d'objet (dictionnaire associant un objet clé à un objet valeur). Les expressions suivantes 

``` python
"Bonjour"  # une chaine de caractères
[0, 1, 2, 9, 16]  # liste de 5 entiers
("Bonjour", "à", "tous")  # n-uplet de 3 chaines de caractères
{12, "Bonjour", None, True, 1.34}  # ensemble de 5 éléments de types différents
{3: "Trois", 10: "Dix", 20: "vingt"} # dictionnaire de 3 associations d'objets
```

- les **types appelables** comme les fonctions (exemple `print`) ou les méthodes
- les **types divers** comme les fichiers, les modules …

La fonction native `type()` renvoie le type de l'objet passé en argument.

```{code-cell} python
type([0, 1, 2, 9, 16])  # renvoie list, le type de l'objet [0, 1, 2, 9, 16]
```

### Muabilité des objets

La muabilité est une propriété des objets qui caractérise leur aptitude à avoir leur valeur modifiée au cours de l'exécution d'une instruction.

- un **objet immuable** (*immutable* en anglais) ne peut jamais changer de valeur. Si ou souhaite une nouvelle valeur, alors il faut utiliser un autre objet. Tous les objets suivants sont des objets immuables :
    - les nombres (entiers, à virgule flottante, complexes, booléens)
    - les chaines de caractères
    - les n-uplets
- un **objet muable** (*mutable* en anglais) peut changer de valeur sans que son identité ne change. Un objet muable peut avoir plusieurs valeurs successives au cours de l’exécution du code source. Tous les objets suivants sont des objets muables :
    - Les listes d'objets
    - Les n-uplets d'objets
    - Les ensembles d'objets
    - Les associations d'objets (dictionnaires)

### Identité d'un objet

Chaque objet possède une identité unique qui ne change jamais au cours de son existence en mémoire, on parle d’identifiant. La fonction native `id()` retourne l’identifiant de l’objet passé en argument. On dit que les objets `a` et `b` ont la même identité s’ils ne font qu’un, c’est-à-dire si l’évaluation de l’expression `id(a) == id(b)` retourne `True`.

```{code-cell} python
id([0, 1, 2, 9, 16])  # renvoie l'identité de la liste [0, 1, 2, 9, 16]
```

### Variables (lien étiquette-objet)

Pour désigner le objet Python dans deux instructions différentes, il est utile de pouvoir le nommer par une étiquette (un lexème de type identifiant dans la grammaire de Python). Dans le code source suivant, l'objet `123` est assigné à l'étiquette `a` dans la 1re instruction `a = 123` ; la 2e instruction désigne l'objet par son étiquette `a` pour la passer comme argument à la fonction `print()`

``` python
a = 123
print(a)
```

Dans le langage Python, les **variables** agissent comme des étiquettes ou des références à des objets en mémoire. Contrairement à certains autres langages de programmation (ex: C, Matlab...) pour lesquels les variables sont des boites (emplacements) contenant des données, en Python, une variable pointe vers un objet qui réside quelque part en mémoire. Une variable (étiquette) réfère (pointe) un et un seul abject ; à l'inverse, un objet peut être assigné à plusieurs variables.


```{figure} img/variable_01.png
---
width: 320px
align: center
---
Représentation graphique d'une liaison nom $\rightarrow$ objet
```

La constitution d'un nom de variable est soumise à des règles impératives issues de la grammaire du langage Python et des conventions fortement recommandées pour faciliter la lecture du code par toute la communauté des développeurs.

Règles de nommage des variables
- *Utiliser uniquement des lettres, des chiffres, et des tirets bas* : un nom de variable est composé de lettres (a-z, A-Z), de chiffres (0-9) et de tirets bas (_)
- *Ne pas commencer par un chiffre* : un nom de variable ne peut pas commencer par un chiffre
- *Ne pas utiliser les mots réservés* : les mots réservés du langage ne peuvent pas être utilisés comme noms de variables, exemples if, for, while, True, False, etc

Conventions de nommage des variables ([PEP8](https://peps.python.org/pep-0008/#function-and-variable-names)])
- [snake case](https://fr.wikipedia.org/wiki/Snake_case) : les noms de variables doivent être en minuscules avec les mots séparés par des tirets bas `_`, exemple `nom_de_variable`
- N'utilisez jamais les caractères `l` (lettre L minuscule) ou `I` (lettre i majuscule) comme noms de variables à caractère unique, car ils se confondent trop facilement selon la police de caractères utilisée. Idem pour le caractère `O` (lettre o majuscule) qui peut se confondre avec le chiffre 0.

### Conteneurs

On appelle **conteneur** un objet Python ayant vocation à en contenir d’autres objets que l'on appelle ses **éléments**. Des exemples de conteneurs sont les chaines de caractères les listes, les ensembles ou les dictionnaires. On dit que `x` est conteneur s’il supporte l'opérateur d'appartenance `in`

- `x in c` renvoie `True` si l'objet `x` est contenu dans le conteneur `c`, sinon `False`
- `x not in c` renvoie `True` si l'objet `x` n'est pas dans le conteneur `c`, sinon `True`. Équivalent à `not (x in c)`

``` python
"o" in "Bonjour"  # renvoi True car le caractère "o" est dans la chaine
"A" in "Bonjour"  # renvoi False car le caractère "A" n'est pas dans la chaine
```

On appelle **longueur** d'un abject de type conteneur le nombre d'éléments qu'il contient. Les conteneurs possèdent la méthode spéciale `__len__()` qui donne leur longueur. Exemples

``` python
"Robotique".__len__()  # donne 9, le nombre de caractères de la chaine "Robotique"
"".__len__()  # donne 0, le nombre de caractères de la chaine vide ""
```

Python propose également une fonction native pour obtenir le nombre d'éléments d'un objet.
- `len(s)` renvoie la longueur (nombre d'éléments) de l'objet `s`. Dans la pratique, `len(s)` renvoie `s.__len__()`.

``` python
len("Robotique")  # donne 9, le nombre de caractères de la chaine
```

### Séquences

On appelle **séquence**, un objet conteneur qui contient des éléments ordonnés. Voici quelques séquences natives : `str` (les chaines de caractères vues précédemment), `list` (les listes), `tuple` (les n-uplets), `range` (les intervalles) ou `bytes` (les séquences d'octets). 

Les séquences sont **itérables**, il existe un protocole pour parcourir leurs éléments un à un (plus de détails à venir dans la section "8.5 Itérables et itérateurs").

Les séquences sont **Indiçable**, il existe un protocole pour atteindre un élément par un nombre entier, un indice.

### Indiçage (indexing)

On appelle l'**indice** (*index* en anglais) d'un élément de séquences, un entier qui caractérise la position de l'élément dans la séquence. Python indice les éléments d'une séquence de deux manières complémentaires :
- l'indice `0` est attribué au premier élément et les éléments suivants sont indicés de manière croissante de 1 en 1,
- l'indice `-1` est attribué au dernier élément et les éléments précédents sont indicés de manière décroissante de -1 en -1.

Les indices positifs et négatifs sont illustrés sur le diagramme ci-dessous sur l'exemple de la chaine de caractères `"Robobique"`.

``` none
|  R |  o |  b |  o |  t |  i |  q |  u |  e | Chaine de caractères (séquence)
|----|----|----|----|----|----|----|----|----|
|  0 |  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 | indices positifs
| -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 | indices négatifs
```

On notera qu'un élément de la séquence est désigné par deux indices distincts, un entier positif et un entier négatif. En revanche, un indice réfère à un et un seul élément, s'il existe. Cela permet de référer à un élément par sa position relative au début de la séquence ou par sa position relative à la fin de la séquence selon les besoins.

On appelle **indiçage** (*indexing* en anglais) l'opération qui désigne un élément dans une séquence à l'aide d'un indice. Python offre un accès efficace aux éléments d'une séquence par les méthodes spéciales `__getitem__()`, `__setitem__()` ou `__delitem__()` selon les besoins. Exemple pour obtenir à un élément :

``` python
"Robotique".__getitem__(2)  # donne 'b', l'élément d'indice 2 de "Robotique"
"Robotique".__getitem__(-5)  # donne 't', l'élément d'indice -5 de "Robotique"
```

Python propose un [sucre syntaxique](https://fr.wikipedia.org/wiki/Sucre_syntaxique) pour l'indiçage, une possibilité d'écriture plus succincte et plus intuitive, en accolant à une instance de séquence l'indice entre crochets. La syntaxe est `objet_de_type_sequence[indice]`. Exemples :

``` python
"Robotique"[2]  # donne 'b', équivalent à "Robotique".__getitem__(2)
"Robotique"[-5]  # donne 't', équivalent à "Robotique".__getitem__(-5)
s = "Robotique"
s[5]  # donne 'i', équivalent à s.__getitem__(5)
```

### Tranchage (slicing)

On appelle **tranche** (*slice* en anglais) une séquence d'indices d'éléments d'une séquence. Python propose le type d'objet `slice` pour représenter les tranches en compréhension, c'est-à-dire sans lister un à un les indices . On peut créer une tranche à l'aide du constructeur d'instances `slice()` des manières suivantes :

- `slice(stop)` renvoie un objet tranche désignant les éléments d'une séquence allant du 1er inclus (indice 0) jusqu'à l'élément d'indice `stop` exclu. Si `stop` est `None` la tranche va jusqu'au dernier élément inclus. 
- `slice(start, stop)` renvoie un objet tranche désignant les éléments d'une séquence allant de l'élément d'indice `start` inclus, jusqu'à l'élément d'indice `stop` exclu. Si `start` est `None` la tranche commence à l'indice 0, si `stop` est `None` tranche va jusqu'au dernier élément inclus.
- `slice(start, stop, step)` renvoie un objet tranche désignant les éléments d'une séquence allant de l'élément d'indice `start` inclus, jusqu'à l'élément d'indice `stop` exclu en progressant par pas de `step` éléments. Si `step` est négatif, la progression se fait en sens inverse.
  - si `step` est positif : si `start` est `None` la tranche commence au premier élément, si `stop` est `None` la tranche va jusqu'au dernier élément inclus.
  - si `step` est négatif : si `start` est `None` la tranche commence au dernier élément, si `stop` est `None` la tranche va jusqu'au premier élément inclus.
  - si `step` est `None`, la tranche progresse d’un élément en un élément.

Exemples :

``` python
slice(7)  # tranche de 0 à 7 exclu (0, 1, 2, 4, 5, 6)
slice(3, 7)  # tranche de 3 à 7 exclu (3, 4, 5, 6)
slice(3, 7, 2)  # tranche de 3 à 7 exclu par pas de 2 (3, 5)
slice(7, 3, -1)  # tranche de 7 à 3 exclu par pas de -1 (7, 6, 5, 4)
slice(7, 3, -2)  # tranche de 7 à 3 exclu par pas de -2 (7, 5)
slice(None)  # tranche désignant tous les éléments
slice(None, 7)  # tranche de 0 à 7 exclu (0, 1, 2, 3, 4, 5)
slice(7, None)  # tranche allant de 7 jusqu'au dernier inclus
slice(None, None, 2)  # tranche allant du premier au dernier inclus, de 2 en 2
slice(None, None, -1)  # tranche allant du dernier au premier inclus
```

Les indices `start` et `stop` peuvent être négatifs, l'un, l'autre ou les deux. Dans ce cas ils désignent les éléments d'une séquence par rapport au dernier élément.

On appelle **tranchage** (*slicing* en anglais) l'opération qui désigne, à l'aide d'une tranche, des éléments dans une séquence. Comme pour l'indiçage, les méthodes spéciales `__getitem__()`, `__setitem__()` ou `__delitem__()` effectuent le tranchage d'une séquence selon les besoins. Exemple :

``` python
"Robotique".__getitem__(slice(7))  # donne 'Robotiq'
"Robotique".__getitem__(slice(3, 7))  # donne 'otiq'
"Robotique".__getitem__(slice(3, 7, 2))  # donne 'oi'
"Robotique".__getitem__(slice(7, 3, -1))  # donne 'uqit'
"Robotique".__getitem__(slice(7, 3, -2))  # donne 'ui'
```

La syntaxe simplifiée avec les crochets `[]` est aussi utilisable avec les tranches. Exemple

``` python
"Robotique"[slice(7)]  # donne 'Robotiq'
"Robotique"[slice(3, 7)]  # donne 'otiq'
"Robotique"[slice(3, 7, 2)]  # donne 'oi'
```

Python propose un [sucre syntaxique](https://fr.wikipedia.org/wiki/Sucre_syntaxique) supplémentaire pour le tranchage avec la syntaxe de crochets `[]`, en remplaçant `[slice(start, stop, step)]` par `[start:stop:step]`.

| Exemple de tranches        | Sucre syntaxique équivalent, uniquement entre `[]` | Commentaire |
|----------------------------|---------------------|---------------------------|
| `slice(stop)`              | `:stop` ou `0:stop` | les `stop` premiers       |
| `slice(start, stop)`       | `start:stop`        | de `start` à `stop` exclu |
| `slice(start, stop, step)` | `start:stop:step`   | de `start` à `stop` exclu, de `step` en `step` |
| `slice(start, None)`       | `start:`            | de `start` jusqu'au dernier inclus |
| `slice(None, stop, step)`  | `:stop:step`        | si `step` > 0, du premier jusqu'à `stop` exclu, de `step` en `step` <br/>si `step` < 0, du dernier jusqu'à `stop` exclu, de `step` en `step` |
| `slice(start, None, step)` | `start::step`       | si `step` > 0, de `start` jusqu'au dernier inclus, de `step` en `step`<br/>si `step` < 0, de `start` jusqu'au premier inclus, de `step` en `step` |
| `slice(None, None, step)`  | `::step`            | si `step` > 0, du premier jusqu'au dernier, de `step` en `step` <br/>si `step` < 0, du dernier jusqu'au premier, de `step` en `step` |

Exemples de tranchage avec l'utilisation des deux sucres syntaxiques

``` python
"Robotique"[:7]  # donne 'Robotiq', équivalent à "Robotique"[slice(7)] ou à
                 # "Robotique".__getitem__(slice(7))
                 
"Robotique"[3:7]  # donne 'otiq', équivalent à "Robotique"[slice(3, 7)] ou à
                  # "Robotique".__getitem__(slice(3, 7))
                  
"Robotique"[3:7:2]  # donne 'oi', équivalent à "Robotique"[slice(3, 7, 2)]
                    # ou à "Robotique".__getitem__(slice(3, 7, 2))
s = "Robotique"
s[::-1]  # donne 'euqitoboR', équivalent à s.__getitem__(slice(None, None, -1))
```

## Instructions simples

Les instructions sont les unités de base qui composent un code Python. Les instructions simples effectuent une action spécifique comme la création d'un objet Python, la gestion des noms dans l'espace de non, la levée d'exception ou le contrôle du flux d'instruction. 


```{list-table} Talbleau des instructions simples
:header-rows: 1

* - Catégorie
  - Instruction simple
* - Création d'objets
  - - expressions
      - opérations arithmétiques (`+`, `-`, `*`, `/`, `**`, `//`, `%`, `@`)
      - opérations sur les bits (opérateur `&`, `|`, `^`, `<<`, `>>`)
      - opérations booléennes (opérateurs `and`, `or`, `not`)
      - comparaisons de valeur (opérateurs `<`, `>`, `==`, `>=`, `<=`, `!=`)
      - comparaisons d'identifiants (opérateurs `is`, `is not`)
      - tests d'appartenance (opérateurs `in`, `not in`)
    - `type` alias de type
* - Gestion de l'espace de nom
  - - assignation simple `=`
    - assignation augmentée `+=`, `-=` , `*=` , `@=` , `/=` , `%=` , `&=` , `|=` , `^=` , `<<=` , `>>=` , `**=` , `//=`
    - `del` suppression d'assignation
    - `import` 
    - `global` pour référer à un nom de la portée globale
    - `nonlocal` pour référer à un nom ni dans la portée globale ni dans la portée locale
* - Levée d'exception
  - - `assert` test de débogage 
    - `raise` déclenchement d'exception 
* - Contrôle de flux d'instructions
  - - `return` sortie définitive d'une fonction
    - `yield` sortie temporaire d'une fonction
    - `break` terminaison prématurée d'instruction de répétition *for* ou d'itération composée *while* la plus imbriquée 
    - `continue` terminaison prématurée de l'itération en cours de l'instruction composée *for* ou *while* la plus imbriquée
* - Autre
  - - `import` importe des objets, des noms d'un autre code source
    - `pass` Opération vide
```

### Expressions

#### Expressions arithmétiques

| Opération | Résultat | 
|-----------|--------- |
| `x + y`   | somme de x et y |
| `x - y`   | différence de x et y | 
| `x * y`   | produit de x et y | 
| `x / y`   | quotient de x par y, résultat de la division | 
| `x ** y`  | x à la puissance y | 
| `-x`      | négatif de x |
| `+x`      | x inchangé | 
| `x // y`  | quotient entier de x par y | 
| `x % y`   | reste de la division de x par y | 


#### Expressions sur les bits

Les opérateurs sur les bits sont souvent utilisés pour manipuler des registres de microcontrôleur, en particulier en informatique embarquée, par exemple dans les projets LDD3 108-208.

| Opération | Résultat |
|-----------|--------- |
| `x \| y`  | "ou" bit à bit de x et y  | 
| `x ^ y`   | "ou exclusif" bit à bit de x et y  | 
| `x & y`   | "et" bit à bit de x et y  | 
| `x << y`  | x décalé vers la gauche de n bits,<br/>équivalent à la multiplication par `pow(2, n)` | 
| `x >> y`  | x décalé vers la droite de n bits,<br/>équivalent à la division par `pow(2, n)` | 
| `~x`      | les bits de x inversés | 

#### Opérations booléennes

Pour construire des expressions booléennes, Python propose trois opérateurs booléens `and` (conjonction), `or` (disjonction) et`not` (négation). Lorsqu'ils opèrent sur des booléens, la sémantique de ces trois opérateurs est présentée dans la table de vérité ci-dessous ; elle est conforme aux usages.

| Résultat de<br/>`exp1` | Résultat de<br/>`exp2` | Résultat de<br/>`exp1 and exp2` | Résultat de<br/>`exp1 or exp2` | Résultat de<br/>`not exp1` |
|---------|---------|---------|---------|---------|
| `True`  | `True`  | `True`  | `True`  | `False` |
| `True`  | `False` | `False` | `True`  | `False` |
| `False` | `True`  | `False` | `True`  | `True`  |
| `False` | `False` | `False` | `False` | `True`  |

#### Comparaisons de valeurs numériques

Python propose six opérateurs pour comparer la valeur de deux objets `<`, `>`, `==`, `>=`, `<=` et `!=` qui permet de construire des expressions de comparaison. Les objets n'ont pas besoin d'être du même type.

| Opération | Résultat |
|-----------|--------- |
| `x == y` |test d'égalité, renvoie `True` si la valeur de `x` est égale à la valeur de `y`, sinon `False`|
| `x != y` |test d'inégalité, renvoie `True` si la valeur de `x` est différente de la valeur de `y`, sinon `False`|
| `x > y` |test de supériorité stricte, renvoie `True` si la valeur de `x` est strictement supérieure de la valeur de `y`, sinon `False`|
| `x >= y`| test de supériorité, renvoie `True` si la valeur de `x` est supérieure ou égale de la valeur de `y`, sinon `False`|
| `x < y` |test d'infériorité stricte, renvoie `True` si la valeur de `x` est strictement inférieure de la valeur de `y`, sinon `False`|
| `x <= y` |test d'infériorité, renvoie `True` si la valeur de `x` est inférieure ou égale de la valeur de `y`, sinon `False`|

#### Priorité des opérateurs

La liste suivante résume les priorités de ces opérateurs, du plus prioritaire (portée la plus courte) au moins prioritaire (portée la plus grande) :

- `(expression...)`,
- opérateurs arithmétiques
    - `**` (puissance), 
    - `-x` `+x` `~` (négatif, positif, inversion bit à bit), 
    - `*` `/` `//` `%` (multiplication, division, division entière, reste), 
    - `+` `-` (addition, soustraction), 
    - `<<` `>>` (décalages), 
    - `&` ("et" bit à bit), 
    - `^` ("ou exclusif" bit à bit), 
    - `|` ("ou" bit à bit)
- opérateurs de comparaison de valeur
    - `<`, `>`, `==`, `>=`, `<=` et `!=` (même priorité)
- opérateurs de comparaison de valeur
    -`<`, `>`, `==`, `>=`, `<=` et `!=` (même priorité)
- opérateurs booléens
    - `not`
    - `and`
    - `or`


### `=` instruction d'assignation 

L'instruction d'**assignation**, ou plus simplement l'assignation, construit l'association entre un nom (étiquette) et un objet. Une fois nommé, un objet pourra être réutilisé autant de fois que nécessaire dans le code. la syntaxe de base d'une instruction d'assignation est

``` python
nom_de_variable = expression
```

et la sémantique (comportement) de l'instruction est la suivante
1. l'`expression` est évaluée et retourne un abject qui est situé dans l'espace des objets Python
2. si l'étiquette `nom_de_variable` n'existe pas dans l'espace des noms, elle est créée
3. l'objet est assigné à l'étiquette `nom_de_variable`, on dit que `nom_de_variable` réfère ou pointe l'objet

Exemple du comportement de 3 assignations successives

| Numéro<br />de ligne| Code | Sémantique | Illustration |
|---------------------|------|------------|--------------|
| 1 | `x = 305` | - `305` est évalué, l'objet de type `int` avec de valeur 300 est créé et retourné<br />- l'étiquette `x` est créée dans l'espace de nom<br />- le lien de l'étiquette vers l'objet est établi | <img src="img/BE1_variable_02.png" width="200px" /> |
| 2 | `y = 305 / 12` | - `305 / 12` est évaluée, l'objet de type `float` avec de valeur 1.5 est créé et retourné<br />- l'étiquette `y` est créée dans l'espace de nom<br />- le lien de l'étiquette vers l'objet est établi | <img src="img/BE1_variable_03.png" width="200px" /> |
| 3 | `x = y` | - `y` est évalué, l'objet pointé est retourné<br />- l'étiquette `x` existe déjà, inutile de la créée dans l'espace de nom<br />- le lien de l'étiquette est redirigé vers l'objet | <img src="img/BE1_variable_04.png" width="200px" /> |

Remarques sur la situation en fin d'exécution des trois assignations
- l'objet `152.5` est assigné à plusieurs variables ou réciproquement, plusieurs noms pointent sur le même objet
- l'objet `305` n’est assigné à aucune variable. Il ne pourra plus être utilisé, et il a pour vocation d'être supprimé de la mémoire par un mécanisme interne à l'interpréteur Python : le ramasse-miette (*garbage collector* en anglais).

Les assignations peuvent prendre plusieurs formes en Langage Python :

1. L'*assignation de base* (vue juste au-dessus)<br />
   syntaxe : `nom_de_variable = expression`<br />
   sémantique : l'`expression` est évaluée, l'objet résultant est assigné à la variable `nom_variable`.
   ``` python
   x = 10 + 2  # assigne l'objet 12 à la variable x
   ```

2. L'*assignation multiple* permet d'assigner des valeurs à plusieurs variables en une seule ligne.<br />
   syntaxe : `nom_1, nom_2, ... nom_n = exp_1, exp_2, ... exp_n`<br />
   sémantique : la partie à droite du signe `=` est évaluée en premier et de gauche à droite, puis les assignations aux variables de la partie gauche se font à leur tour de gauche à droite. Cela donne la séquence suivante - évaluation de `exp_1`, évaluation de `exp_2`, ... évaluation de `exp_n`, assignation à `nom_1` de l'objet obtenu après l'évaluation de `exp_1`, assignation à `nom_2` de l'objet obtenu après l'évaluation de `exp_2`, ... assignation à `nom_n` de l'objet obtenu après l'évaluation de `exp_n`<br />
   ```python
   x, y = 305, "Bonjour"  # 305 est assigné à x, "Bonjour" est assigné à y
   x, y = y, x  # échange les objets pointés par les variables x et y
   ```

3. l'*assignation chainée* permet de lier plusieurs variables au même objet.<br />
   syntaxe : `nom_1, nom_2, ... nom_n = expression`<br />
   sémantique : l'`expression` est évaluée, l'objet résultant est assigné successivement aux variables de la partie gauche dans l'ordre de gauche à droite.<br />
   ```python
   x = y = z = 10  # x, y, et y pointent toutes vers le même objet 10
   ```

4. l'*assignation augmentée* permet de réaliser une opération et une assignation simultanément, ce qui est utile pour modifier la valeur d'une variable basée sur sa valeur courante.<br />
   syntaxe : `nom_de_variable ∴= expression`<br /> ou `∴` ∈ {`+`, `-`, `*`, `@`, `/`, `//`, `%`, `**`, `>>`, `<<`, `&`, `^`, `|`}<br />
   sémantique : un assignation augmentée peut se réécrire comme l'assignation de base suivante `nom_de_variable = nom_de_variable ∴ expression`, et elle en a la même sémantique<br />
   ```python
   x = 355
   x -= 50  # équivalent à x = x - 50, x pointe maintenant sur l'entier 305
   ```

### `del` instruction de suppression

L'instruction de **suppression** détruit des noms (étiquette) et leur association des objets Python. Elle joue le rôle inverse de l’instruction d'assignation, elle est importante lorsque l'on souhaite libérer de l'espace en mémoire. La syntaxe de base d'une instruction de suppression est

``` python
del nom_1, nom_2 ... nom_n
```

et la sémantique (comportement) de l'instruction de suppression est : suppression de gauche à droite des `nom_i` et de leur lien avec les objets Python.

Exemple du comportement de quelques instructions

| Numéro<br />de ligne| Code | Sémantique | Illustration |
|---------------------|------|------------|--------------|
| 1<br />2 | `x = y = "Bonjour"`<br>`z = -432` | - `"Bonjour"` est créé et assigné au nom `x` et `y` | <img src="img/BE1_del_01.png" width="200px" /> |
| 3 | `del y` | - suppression du nom `y` | <img src="img/BE1_del_02.png" width="200px" /> |
| 4 | `del x, z` | - suppression des noms `x` et `z` | <img src="img/BE1_del_03.png" width="200px" /> |

Remarque : l'instruction `del` supprime des noms, pas des objets ; lorsque plus aucun nom ne réfère à un objet Python, ce dernier devient inatteignable et il a pour vocation d'être supprimé de la mémoire par un mécanisme interne à l'interpréteur Python, le  **ramasse-miette** (garbage-collector en anglais). 


### `raise` levée d'exception

En Python, une exception est un évènement qui interrompt le flux normal d'exécution d'un code source lorsqu'une erreur ou une condition exceptionnelle se produit. L'interpréteur commence à rechercher un gestionnaire d'exception approprié (instruction composée `try` ... `except`) dans l'ordre inverse de la pile d'appels des instructions (*traceback* en anglais). Si aucun gestionnaire d'exception n'est trouvé, l'interpréteur arrête le programme et affiche un message d'erreur de traceback. Ce message inclut des informations sur l'exception levée, la pile d'appels au moment de l'exception, et le type et le message de l'exception.

L'instruction raise permettre de levée explicitement une exception.

syntaxe 1 : `raise`<br />
sémantique : `raise` propage l'exception en cours de traitement, aussi dénommée exception active. Si aucune exception n'est active, une exception `RuntimeError` est levée, indiquant que c'est une erreur.

```{code-cell} python
raise
```
syntaxe 2 : `raise <expression>`<br />
sémantique : `raise`  évalue 'la première l'expression `<expression>` en tant qu'objet exception. Ce doit être une sous-classe ou une instance de `BaseException`. Si c'est une classe, l'instance de l'exception est obtenue en instanciant la classe sans argument (au moment voulu). Le type de l'exception est la classe de l'instance de l'exception, la value est l'instance elle-même.

```{code-cell} python
raise Exception("Mon exception")
```

### `assert` test de débogage

Les instructions assert sont une manière pratique d'insérer des tests de débogage au sein d'un code source

syntaxe 1 : `assert <expression_de_test>`<br />
sémantique : ne faire rien si `<expression_de_test>` vaut `True`, sinon lève l'exception `AssertionError`.

syntaxe 2 : `assert <expression_de_test>, <chaine_de_caracteres>`<br />
sémantique : ne faire rien si `<expression_de_test>` vaut `True`, sinon lève l'exception `AssertionError` avec le message <chaine_de_caracteres>

Exemples

```{code-cell} python
a = 1
assert a == 1, "valeur incorrecte pour a"
```

```{code-cell} python
a = 3
assert a == 1, "valeur incorrecte pour a"
```

### `pass` opération vide

Quand `pass` est exécutée, rien ne se passe. Elle est utile comme bouche-trou lorsqu'une instruction est syntaxiquement requise, mais qu'aucun code ne doit être exécuté. Par exemple :

``` python
if a < 0:
    pass  # TODO: prévoir un traitement pour gérer les valeurs négatives
```

### `import` importation de modules

L'importation de modules en Python joue un rôle crucial dans la modularité et la réutilisabilité du code source, elle permet :
- la réutilisation de code existant sans avoir à le réécrire. Par exemple, le module `math` fournit des fonctions mathématiques couramment utilisées, telles que `sin()`, `cos()`, et des données comme `pi`.
- la structuration du code en le répartissant dans plusieurs modules stockés dans des fichiers distincts, puis importés selon les besoins.
- l'encapsulation des fonctions et des variables, chaque module a sa propre *portée* dans l'espace de noms, ce qui permet d'éviter les collisions de noms entre les différents modules et le code source principal. 
 
Une **portée** est une étendue de l'espace des noms qui est accessible par défaut aux instructions d'un code. Le code du programme principal crée et accède à des noms dans la portée que l'on nommera "main (global)" tandis que le code d'un module "nom_du_module" crée et accède à des noms dans la portée "nom_du_modul (global)"

Quand un module est importé pour la première fois, Python recherche le module et, s'il est trouvé, crée un objet module en l'initialisant. Si le module n'est pas trouvé, une exception `ModuleNotFoundError` est levée. Python implémente plusieurs stratégies pour rechercher le module d'un nom donné quand le mécanisme d'importation est invoqué (par exemple dans le chemin des bibliothèques de la distribution Python ou dans l'emplacement du code source en cours d'exécution).

Syntaxe 1 : `import <nom_module>`<br />
sémantique : trouve un module `<nom_module>`, le charge et l'initialise si nécessaire puis définit le nom `<nom_module>` dans la portée où l'instruction `import` apparait. 

``` python
import math 
math.pi  # accès à un objet dans le module math avec la notation pointée
```

Exemple d'évolution de l'espace des objets et de l'espace des noms avec le code suivant

``` python
import math
a = math.pi / 6
b = math.sin(a)
```

```{list-table} 
:header-rows: 1
:widths: 20 80

* - Ligne de code
  - Sémantique et illustration

* - `import math`
  - - le module `math` est créé dans l'espace des objets
    - il est initialisé (exécuté) ce qui génère des objets dans l'espace des objets est des noms dans sa portée propre dans l'espace des noms. Par souci de lisibilité, seuls le flottant `pi` et la fonction `sin()` du module `math` sont représentés.

    Dans l'illustration, on voit apparaitre deux *portées*, une désignée par "main (global)" pour le code principal (qu'on ne faisait pas apparaitre jusqu'ici) et une désignée par "math (global)" pour le code du module `math`. Le lien entre l'objet module `math` et sa portée est illustré par une flèche en trait discontinu.

    <img src="img/import_01a.png" width="400px" />

* - `a = math.pi / 6`
  - L'objet désigné par `math.pi` est l'objet pointé par `pi` depuis la portée "math (globale)" du module pointé par `math` depuis la portée principale où s'exécute l'instruction `a = math.pi / 6`, c'est-à-dire "main (global)". Cet objet est divisé par l'objet `6` et l'objet produit est assigné au nom `a` dans la portée principale.
    
    <img src="img/import_01b.png" width="400px" />

* - `b = math.sin(a)`
  - L'objet `a` (accessible depuis la portée principale) est passé en argument à la fonction `sin()` (accessible depuis la portée du module `math` avec la notation pointée `math.sin()`) ; l'objet `0.5` est renvoyé par la fonction et il est assigné au nom `b` dans  l'espace de nom principal.

    <img src="img/import_01c.png" width="400px" />

```
<br />

Syntaxe 2 : `import <nom_module> as <nom_d_alias>`<br />
sémantique : trouve un module `<nom_module>`, le charge et l'initialise si nécessaire puis définit le nom `<nom_d_alias>` dans la portée où l'instruction `import` apparait. 

Exemple :

``` python
import numpy as np
np.euler_gamma  # accès au flottant γ=0.57721 du module numpy
```

L'illustration met en évidence l'organisation de l'espace des noms après l'exécution des deux instructions précédentes. On voit que le module `numpy` pourra uniquement être utilisé à partir du nom `np` depuis la portée du programme principal. 

<img src="img/import_02.png" width="400px" /><br />



Syntaxe 3 : `from <nom_module> import <nom_1>, <nom_2>, ... <nom_n>`<br />
sémantique : trouve un module `<nom_module>`, le charge et l'initialise si nécessaire puis, définit dans l'espace des noms locaux les noms `<nom_n>` qui sont assignés aux objets de même nom du module `<nom_module>`. 

Exemple :

``` python
from math import pi, sin
```

On voit sur l'illustration suivante que le module `math` n'a pas de nom assigné dans la portée du programme principal. Hormis la fonction `sin()` et le flottant `3.14...` auxquels le programme principal peut accéder par les noms `sin` et `pi` dans sa portée, les autres objets du module sont inaccessibles.

<img src="img/import_03.png" width="400px" />


## Instructions composées

Les instructions composées contiennent d'autres (groupes d’) instructions ; elles affectent ou contrôlent l'exécution de ces autres instructions d'une manière ou d'une autre. Parmi les instructions composées, on peut citer :
- les conditions `if`
- les itérations `for`
- les répétitions `while`
- les définitions de fonction `def`
- les définitions de classe `class`
- ...

La figure suivante illustre la syntaxe d'une instruction composée.
- Une instruction composée comporte une ou plusieurs "clauses"
- Une clause se compose d'un entête et d'une "suite"
- Chaque entête de clause commence par un "mot-clé" spécifique et se termine par le caractère deux-points `:`
- Une "suite" est un groupe d'instructions contrôlées par une clause

```{image} img/BE1_instruction_composee_01.png
:width: 300px
:align: center
```

Les entêtes des clauses d'une instruction composée particulière sont tous placés au même niveau d'indentation.

Les suites se composent d'une ou plusieurs instructions en retrait (niveau d'indentation supplémentaire) sur les lignes suivantes. Comme les suites ne peuvent être vides, il est utile de disposer d'une instruction bouche-trou pour conserver la cohérence syntaxique d'une instruction composée, parfois même temporairement pour faire de premiers tests d'exécution. L'instruction simple `pass` est l'opération vide ; quand elle est exécutée, rien ne se passe.

```{list-table} Talbleau des instructions simples
:header-rows: 1

* - Catégorie
  - Instruction composée
* - Contrôle de flux d’instructions
  - - `if` exécution après comparaison
    - `while` répétition conditionnelle
    - `for` itération
    - `match` filtrage par motif
* - Création d'objets
  - - `def` définition d'une fonction
    - `async def` définition d'une coroutines
    - `class` définition d'une classe
* - Gestion d'environnement
  - - `with` gestionnaire de contextes
    - `try` gestionnaire d'exception
```

### `if` exécution conditionnelle

L'instruction `if` est utilisée pour exécuter des instructions en fonction d'une condition

Syntaxe : l'instruction composée `if` est contituée de :
- 1 clause "if" : `if <expression_de_test>: <suite>`
- 0 à n clauses "elif" : `elif <expression_de_test>: <suite>`
- 0 à une clause "else" : `else: <suite>`

Sémantique : L'instruction composée `if` sélectionne exactement une des suites en évaluant les expressions `<expression_de_test>` une par une jusqu'à ce qu'une soit vraie. Ensuite cette `<suite>` est exécutée (et aucune autre partie de l'instruction if n'est exécutée ou évaluée) Si toutes les expressions `<expression_de_test>` sont fausses, la suite de la clause "else", si elle existe, est exécutée. 

Exemple :

```{code-cell} python
x = 12
# ═════ début d'une instruction composée ═══╗
#┌──────── début d'une clause  ───────────┐ ║
if x < 0:             # <-- entête        │ ║
    print("négatif")  # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
#┌──────── début d'une clause  ───────────┐ ║
elif x == 0:          # <-- entête        │ ║
    print("nul")      # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
#┌──────── début d'une clause  ───────────┐ ║
else:                 # <-- entête        │ ║
    print("positif")  # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
# ══════════════════════════════════════════╝  
```

### `for` itérations

L'instruction composée `for` est utilisée pour itérer sur les éléments d'une séquence (par exemple une chaine, un n-uplet ou une liste) ou un autre objet itérable

Syntaxe : l'instruction composée `for` est constituée de :
- 1 clause "for" : `for <nom_cible> in <expression>: <suite>`
- 0 à une clause "else" : `else: <suite>`

Sémantique : L'expression `<expression>` n'est évaluée qu'une seule fois ; elle doit produire un objet itérable. Un itérateur est créé pour cet itérable. Le premier élément produit par l'itérateur est assigné au nom à la liste cible `<nom_cible>`, puis la `<suite>` est exécutée. Lorsque les éléments de l'itérateur sont épuisés, la `<suite>` de la clause "else", si elle existe, est exécutée et la boucle se termine.
- Une instruction `break` exécutée dans la première suite termine la boucle sans exécuter la suite de la clause "else". 
- Une instruction `continue` exécutée dans la première suite saute le reste de la suite et continue avec l'élément suivant, ou avec la clause "else" s'il n'y a pas d'élément suivant.

Exemple :

```{code-cell} python
# ═════ début d'une instruction composée ═══╗
#┌──────── début d'une clause  ───────────┐ ║
for i in range(4):    # <-- entête        │ ║
    print(f"{i = }")  # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
#┌──────── début d'une clause  ───────────┐ ║
else:                 # <-- entête        │ ║
    print("fin !")    # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
# ══════════════════════════════════════════╝  
```

### `while` répétition conditionnelle

L'instruction composée `while` est utilisée pour exécuter des instructions de manière répétée tant qu'une expression est vraie :

Syntaxe : l'instruction composée `while` est constituée de :
- 1 clause "while" : `for <expression_de_test>: <suite>`
- 0 à une clause "else" : `else: <suite>`

Sémantique : L'expression `<expression_de_test>` est évaluée manière répétée et, tant qu'elle est vraie, exécute la première suite ; si l'expression est fausse (ce qui peut arriver même lors du premier test), la suite de la clause "else", si elle existe, est exécutée et la boucle se termine.
- Une instruction `break` exécutée dans la première suite termine la boucle sans exécuter la suite de la clause "else". 
- Une instruction `continue` exécutée dans la première suite saute le reste de la suite et retourne au test de l'expression `<expression_de_test>`

Exemple :

```{code-cell} python
i = 4
# ═════ début d'une instruction composée ═══╗
#┌──────── début d'une clause  ───────────┐ ║
while i > 0:          # <-- entête        │ ║
    print(f"{i = }")  # ├─ suite indentée │ ║
    i = i -1          # │                 │ ║
#└────────────────────────────────────────┘ ║
#┌──────── début d'une clause  ───────────┐ ║
else:                 # <-- entête        │ ║
    print("fin !")    # <- suite indentée │ ║
#└────────────────────────────────────────┘ ║
# ══════════════════════════════════════════╝  
```

### `def` définition d'un fonction

Voir [fonctions utilisateur](./2b_fonction_python.md)

### `class` définition d'une classe d'objet 

Voir [classes utilisateur](./3b_classe_python.md)


## Fonctions natives

Les fonctions natives sont les fonctions du module `builtins`. Pour y accéder, inutile d'importer le module, celui-ci est importé chaque fois qu'un code source est exécuté soit depuis un fichier soit en ouvrant une session interactive par exemple avec Jupyter. La portée de ce module contient entre autres des fonctions, des classes ou des constantes.


```{figure} img/import_04.png
---
width: 180px
align: center
---
Illustration de la portés principale d'un code source "main (global)" placée dans la portée du module "(builtins)" dès le début du programme.
```

Pour rechercher un nom dans l'espace des noms, Python recherche séquentiellement en commençant par la portée correspondant au code qu'il exécute, puis les portées englobantes, jusqu'à la portée "builtins". Si le nom existe, alors Python retient la première occurrence de celui-ci. Sinon, il lève une exception de type `NameError`.



```{list-table} Talbleau des fonctions native
:header-rows: 1

* - Catégorie
  - fonctions natives
* - Opérations mathématiques
  - - `abs()` renvoie la valeur absolue d'un nombre
    - `divmod()` renvoie le quotient et le reste de la division entière
    - `max()` renvoie le plus grand des arguments ou éléments donnés dans un itérable
    - `min()` renvoie le plus petit des arguments ou éléments donnés dans un itérable
    - `pow()` renvoie un nombre à une puissance donnée
    - `round()` renvoie une valeur arrondie
    - `sum()` renvoie la somme des valeurs d'un itérable
* - Instanciations d'une classe d'objets
  - - `int()` construit un nombre entier à partir d'un nombre ou d'une chaine de caractères
    - `float()` construit un nombre à virgule flottant à partir d'un nombre ou d'une chaine
    - `complex()` construit un nombre complexe à partir d'arguments
    - `str()` construit une chaine de caractères
    - `bool()` construit un nombre booléen
    - `bytes()` construit un tableau immuable d'octets
    - `bytearray()` construit un tableau modifiable d'octets
    - `list()` construit une liste d'objets
    - `tuple()` construit un n-uplet d'objets
    - `dict()` construit une suite de paires clé-valeur
    - `set()` construit un ensemble modifiable d'objets 
    - `frozenset()` construit un ensemble immuable d'objets
    - `range()` construit un intervalle de nombres entiers
    - `slice()` construit une tranche d'indice 
    - `iter()` construit un itérateur sur un itérable
    - `memoryview()` construit une vue mémoire créée depuis l'argument
    - `object()` construit un objet vide. objet est la classe parente de toutes les classes
* - Conversions
  - - `bin()` convertit un entier en sa représentation binaire dans une chaine avec le préfixe "0b"
    - `oct()` convertit un entier en sa représentation octale dans une chaine préfixée de "0o"
    - `hex()` convertit un entier en sa représentation hexadécimale dans une chaine préfixée de "0x"
    - `format()` convertit une valeur en sa représentation formatée
    - `ord()` renvoie le point de code d'un caractère
    - `chr()` renvoie le caractère à partir de son point de code
* - Gestion des entrées-sorties
  - - `print()` affiche les arguments sur la console
    - `open()` ouvre un fichier et donne accès à un objet de fichier
    - `input()` lire l'entrée de la console
* - Traitements d'itérables
  - - `len()` renvoie la longueur (nombre d'éléments) d'un objet
    - `reversed()` renvoie un itérateur inverse depuis un objet
    - `sorted()` renvoie une nouvelle liste triée depuis un itérable
    - `all()` renvoie True si tous les éléments de l'itérable sont vrais
    - `any()` Renvoie True si au moins un élément de l'itérable est vrai
    - `enumerate()` renvoie un objet itérable qui renvoie un n-uplet contenant un compteur (démarrant à 0 par défaut) et les valeurs obtenues de l'itération sur l'itérable passé en argument.
    - `zip()` itère sur plusieurs itérables en parallèle, produisant des n-uplets avec un élément provenant de chacun
    - `next()` donne l'élément suivant de l'itérateur
    - `filter()` construit un itérateur depuis les éléments de l'itérable fourni en argument pour lesquels une fonction fournie renvoie True
    - `map()` renvoie un itérateur appliquant une fonction fournie en argument à chaque élément de l'itérable
* - Gestion des classes, des objets et des attributs
  - - `hash()` renvoie la valeur de hachage d'un objet
    - `property()` renvoie un attribut propriété
    - `classmethod()` transforme une méthode en méthode de classe
    - `staticmethod()` transforme une méthode en méthode statique
    - `getattr()` renvoie la valeur d’un attribut
    - `setattr()` assigne une valeur à un attribut 
    - `delattr()` supprime un attribut
    - `hasattr()` renvoie True l'attribut nommé est dans objet
    - `isinstance()` renvoie True si l'objet donné est une instance de la classe donnée
    - `issubclass()` renvoie True si la classe donnée est une sous-classe de la classe donnée
    - `callable()` renvoie True si l'objet en argument est appelable (*callable* en anglais)
    - `super()` renvoie un objet mandataire déléguant les appels de méthode à une classe parente
* - Accès à des noms
  - - `locales()` renvoie un dictionnaire représentant la table des symboles locaux
    - `globals()` renvoie le dictionnaire implémentant l'espace de nommage du module actuel
* - Introspection d'objet
  - - `id()` renvoie l'identité d'un objet
    - `type()` renvoie le type d'un objet
    - `dir()` renvoie la liste des attributs d'un objet
    - `vars()` renvoie l'attribut `__dict__` d'un module, d'une classe, d'une instance ou de n'importe quel objet avec un attribut `__dict__`
* - Gestion de code
  - - `eval()` analyse et évalue comme une expression Python fourni en paramètre
    - `exec()` exécution dynamique de code Python fourni en paramètre
    - `compile()` traduit le code source passé en paramètre en un objet code
* - Autres
  - - `help()` invoque le système d'aide natif 
    - `repr()` renvoie une représentation d'un objet en chaine de caractère conviviale
```

