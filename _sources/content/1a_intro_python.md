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

# Introduction à Python

## Introduction

**Python** est un langage de programmation interprété, de haut niveau et polyvalent. Il est reconnu pour sa syntaxe simple et lisible, ce qui en fait un excellent choix pour les débutants comme pour les codeurs et les codeuses expérimentés. Python supporte plusieurs paradigmes de programmation, tels que la programmation procédurale (impérative), orientée objet ou fonctionnelle. Il est utilisé dans de nombreux domaines, comme le développement web, l'automatisation de tâches, la science des données, l'intelligence artificielle, et plus encore, grâce à ses bibliothèques riches et son écosystème étendu.

```{image} img/logo_python_with_text.png
:width: 360px
:align: center
```

Le langage Python est décrit par des règles de syntaxe pour écrire des **instructions** et par des règles de sémantique pour définir les actions produites par les instructions sur des **objets** (données) en mémoire de la machine, parfois en lien avec des périphériques (clavier, terminal, réseau, système de fichier). On appellera **code source**, parfois simplement code lorsqu'il n'y aura pas d'ambigüité, une suite d'instructions rédigées selon les règles de la syntaxe du langage Python et agrémentée de commentaires. Voici un exemple de code source Python proposé sur la page d'accueil du site [python.org](https://python.org/) et suivi du résultat de son exécution.


```{code-cell} python
def fib(n):
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a + b
    print()
fib(1000)
```

Le langage Python est dit interprété, en opposition aux langages dits compilés, parce qu'il nécessite une application nommée **interpréteur Python** pour générer et exécuter au fur et à mesure un code compréhensible par machine à partir des instructions du code source. Les langages compilés utilisent, en amont de l'exécution, une application nommée compilateur (en réalité une suite d'outils) pour traduire le code source en un code compréhensible par machine et qui pourra être ultérieurement exécuté de manière autonome par la machine. Les codes compilés sont généralement plus rapides à l'exécution que les codes interprétés alors que les codes interprétés sont plus rapides à développer et mettre au point. Parmi les langages interprétés on trouve Julia, JavaScript, Matlab, PHP, Python, R ou Ruby et parmi les langages compilés on trouve comme C, C++, c#, Go, Fortran, Haskell ou Rust.

```{admonition} Notions clés
Un **code source** en langage Python est un texte du décrit un ensemble d'**instructions** écrites selon des règles de **syntaxe** et qui produisent des actions conformément à leur **sémantique** grâce à l'**interpréteur Python**. Le code source peut également contenir des commentaires.
```


## Langage Python

La syntaxe d'un code source en langage Python est définie par une **grammaire formelle** (disponible ici : https://docs.python.org/fr/3/reference/grammar.html) qui spécifie comment un axiome et des symboles non terminaux sont construits à partir de symboles terminaux et de règles de productions. Concrètement,
- **l'axiome** représente l'ensemble des instructions d'un code source Python, et
- **les symboles terminaux** sont des éléments lexicaux (lexèmes) comme des mots-clés, des nombres, des identifiants, des opérateurs... 

Pour interpréter un code source, il faut commencer par une **analyse lexicale** qui identifie les lexèmes et accessoirement élimine les commentaires et les lignes vides, puis continuer par une **analyse syntaxique** en s'appuyant sur la grammaire pour identifier les instructions et leur structure.

### Commentaires

Les commentaires en Python commencent avec un caractère croisillon, #, et s'étendent jusqu'à la fin de la ligne. Un commentaire peut apparaitre dès le début d'une ligne ou après un ou plusieurs espaces, ou à la suite d'un fragment de code, mais pas à l'intérieur d'une chaine de caractères littérale. Un caractère croisillon à l'intérieur d'une chaine de caractères est juste un caractère croisillon. Exemples :

``` python
# Ce commentaire occupe toute la ligne
     # Ce commentaire débute après quelques espaces
a = 123  # Ce commentaire fait suite au fragment de code "a = 123"
s = "Suivez le hashtag #python"  # le 1er # fait parti d'une chaine
```

La grammaire formelle qui décrit la syntaxe du langage n'intègre pas les commentaires. Ils sont donc tout simplement éliminés par l'interpréteur Python avant de lire les instructions. 

Les principales utilisations des commentaires sont :

- planifier les futures nouvelles parties de votre code. Ne pas oublier pas de supprimer ces commentaires une fois que le code est écrit

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

### Lexèmes

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

### Objets Python

Avec Python toutes les données sont représentées sous forme d’objets. Un objet est une entité stockée dans la mémoire de la machine hôte, qui possède :
- une valeur
- un type (nommée aussi classe)
- une identité
- et éventuellement des attributs-données (ou simplement attributs) et des attributs-méthodes (ou simplement méthodes)

La figure suivante illustre graphiquement la notion d’objet Python. À droite, une version détaillée qui montre tout ce qui est encapsulé dans l’objet (sa valeur, son type, son identité, ses attributs-données et ses attributs-méthodes) et à gauche une représentation compacte avec juste son type et sa valeur.

```{figure} img/objet_01.png
---
width: 300px
align: center
---
Représentations graphiques d'un objet Python<br />version détaillée (à gauche), version compacte (à droite)
```

#### Types d'objet

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

#### Muabilité des objets

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

#### Identité d'un objet

Chaque objet possède une identité unique qui ne change jamais au cours de son existence en mémoire, on parle d’identifiant. La fonction native `id()` retourne l’identifiant de l’objet passé en argument. On dit que les objets `a` et `b` ont la même identité s’ils ne font qu’un, c’est-à-dire si l’évaluation de l’expression `id(a) == id(b)` retourne `True`.

```{code-cell} python
id([0, 1, 2, 9, 16])  # renvoie l'identité de la liste [0, 1, 2, 9, 16]
```

#### Variables (lien étiquette-objet)

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

### Instructions simples

Les instructions sont les unités de base qui composent un code Python. Les instructions simples effectuent une action spécifique comme la création d'un objet Python, la gestion des noms dans l'espace de non, la levée d'exception ou le contrôle du flux d'instruction. 


```{list-table} Talbleau des instructions simples
:header-rows: 1

* - Catégorie
  - Instruction simple
* - Création d'objets
  - - expressions
      - opérations arithmétiques (`+`, `-`, `*`, `/`, `**`, `//`, `%`, `@`)
      - opérations booléennes (opérateurs `and`, `or`, `not`)
      - opérations bit à bit (opérateur `&`, `|`, `^`, `<<`, `>>`)
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

#### `=` instruction d'assignation 

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

#### `del` instruction de suppression

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

#### `raise` levée d'exception

```{code-cell} python
print("coucou")
raise Exception("Test d'exception")
print("coucou2")

```

### Instructions composées

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
```

Les entêtes des clauses d'une instruction composée particulière sont toutes placées au même niveau d'indentation.

Les suites se composent d'une ou plusieurs instructions en retrait (niveau d'indentation supplémentaire) sur les lignes suivantes. Comme les suites ne peuvent être vides, il est utile de disposer d'une instruction bouche-trou pour conserver la cohérence syntaxique d'une instruction composée, parfois même temporairement pour faire des premiers tests d'exécution. L'instruction simple `pass` est l'opération vide ; quand elle est exécutée, rien ne se passe.

```{list-table} Talbleau des instructions simples
:header-rows: 1

* - Catégorie
  - Instruction composée
* - Contrôle de flux d’instructions
  - - `if` exécution comparaison
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

### Fonctions natives

Les fonctions natives sont les fonctions du module `builtins` qui est automatiquement chargé au lancement de l'interpréteur Python. 

```{list-table} Talbleau des fonctions native
:header-rows: 1

* - Catégorie
  - fonctions natives
* - Opération mathématiques
  - - `abs()` renvoie la valeur absolue d'un nombre
    - `divmod()` renvoie le quotient et le reste de la division entière
    - `max()` renvoie le plus grand des arguments ou éléments donnés dans un itérable
    - `min()` renvoie le plus petit des arguments ou éléments donnés dans un itérable
    - `pow()` renvoie un nombre à une puissance donnée
    - `round()` renvoie une valeur arrondie
    - `sum()` renvoie la somme des valeurs d'un itérable
* - Instanciation d'une classe d'objets
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
    - `object()` construit un objet vide. object est la classe parente de toutes les classes
* - Conversion
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
* - Traitement d'itérable
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
    - `issubclass()` renvoie True si la classe donnée est une sous classe de la classe donnée
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

## Interpréteur Python

Un interpréteur Python est une application informatique qui exécute les instructions d'un code source écrit en langage Python. L'exécution d'une instruction peut :
- créer, modifier, supprimer des objets Python (données) dans l'espace des objets en mémoire de la machine
- assigner un objet à un nom
- produire des sorties (à l'écran, dans un fichier, sur le réseau...)
- prendre en compte des entrées (depuis le clavier, un fichier, un réseau...)

```{image} img/interpreteur.png
:width: 360px
:align: center
```

### Rôle d'un interpréteur Python

- **Analyser et exécuter du code** - l'interpréteur lit le code source écrit en Python, le traduit en un code intermédiaire (*bytecode* en anglais), et l'exécute immédiatement.
- **Gérer de la mémoire** - l'interpréteur gère la mémoire en allouant et libérant l'espace nécessaire pour les objets (données) via un mécanisme de ramasse-miettes (*garbage collection* en anglais).
- **Gérer des erreurs** - l'interpréteur identifie les erreurs syntaxiques ou d'exécution et affiche des messages d'erreur appropriés, ce qui facilite le débogage du programme.
- **Fournir un environnement interactif** - l'interpréteur permet aux codeurs de tester du code ligne par ligne dans un environnement interactif, comme le REPL (*Read-Eval-Print Loop*). Cela permet de rapidement tester des idées ou de comprendre comment une partie spécifique du code fonctionne.

### Exemples d'interpréteur Python

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

### Fonctionnement d'un interpréteur Python

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

## Bibliothèques

Comme tous les langages informatiques, le langage Python offre un nombre limité de fonctionnalités essentielles. Les bibliothèques sont là pour apporter de nouvelles fonctionnalités plus riches et d'un usage courant. 

### Bibliothèque standard Python

La bibliothèque standard est la bibliothèque distribuée avec Python, elle offre un éventail de plus de 200 modules, dont le module `builtins` qui est automatiquement chargé au lancement de l'interpréteur Python pour fournir les fonctions natives, comme `print()`, `format()`, `len()`, `min()` ou encore `max()`. 

L'instruction d'importation sert à charger les modules, sa syntaxe utilise les mots-clés `import`, `from` et `as`. L'exemple suivent d'un code à deux instructions présentes 1. l'importation du module `math` qui fournit l'accès à des fonctions mathématiques 2. l'utilisation de la fonction trigonométrique `sin()` du module `math`.

``` python
import math  # importation du module math
y = math.sin(0.1)  # assigne à y la valeur du sinus de 0.1 radian
```

Les modules de la bibliothèque standard proposent des fonctions mathématiques (ex. : `math`, `decimal`, `fractions`, `random`, `statistics`), des d'accès aux services du système d'exploitation (ex. : `os`, `time`, `logging`), des communications et de traitements de données provenant d'internet (ex. : `socket`, `email`, `html`, `webbrowser`,`json`), des d'interfaces utilisateur graphiques à base de fenêtres, menus, boites de dialogue (ex: `tkinter`) ... La liste exhaustive des modules de la bibliothèque standard avec leurs documentations est disponible sur la page https://docs.python.org/fr/3/library

```{image} img/logo_modules_python.png
:width: 280px
:align: center
```

### Bibliothèques tierces

Les bibliothèques tierces pour Python sont des collections de modules et de fonctions créées par des développeurs et des développeuses externes à l'équipe principale de Python. Elles étendent les fonctionnalités de base du langage pour répondre à des besoins spécifiques dans différents domaines.


::::{grid}
:gutter: 2

:::{grid-item-card}
```{image} img/logo_numpy.png
:width: 360px
:align: left
```
[NumPy](https://numpy.org/) fournit des matrices ou tableaux multidimensionnels ainsi que des fonctions opérant sur ces tableaux comme des fonctions mathématiques ou logiques, les tris, les sélections, les statistiques de base...
:::

:::{grid-item-card}
```{image} img/logo_matplotlib.png
:width: 360px
:align: left
```
[Matplotlib](https://matplotlib.org/) permet de visualiser des données en créant des graphiques statiques, animés ou interactifs , en 2D et en 3D, comme les courbes, les nuages de points, les contours de champs, les diagrammes de flux, les distributions statistiques...
:::

:::{grid-item-card}
```{image} img/logo_scipy.png
:width: 360px
:align: left
```
[SciPi](https://scipy.org/) propose des algorithmes d'optimisation, d'intégration, d'interpolation, de recherche de valeurs propre, de résolution d'équations algébriques et différentielles, de traitement du signal, de traitement d'images...
:::

::::

::::{grid}
:gutter: 2

:::{grid-item-card}
```{image} img/logo_pandas.png
:width: 360px
:align: left
```
[Pandas](https://pandas.pydata.org/) permet la manipulation et l'analyse de données structurées en tableaux à deux dimensions et de en séries temporelles. Il gère entre autres les fichiers CSV et MS Excel.
:::

:::{grid-item-card}
```{image} img/logo_scikit_learn.png
:width: 360px
:align: left
```
[Pandas](https://pandas.pydata.org/) propose de l'apprentissage machine avec les forêts d'arbres décisionnels, les régressions logistiques, les classements automatiques ou les machines à vecteurs de support.
:::

:::{grid-item-card}
```{image} img/logo_tensorflow_2.png
:width: 360px
:align: left
```
[TensorFlow](https://www.tensorflow.org/) permet de créer et entrainer des modèles d'apprentissage machine avec en particulier avec des réseaux de neurones profonds. Il est capable d'utiliser des GPU pour accélérer les calculs et  déployer les modèles sur différentes plateformes.
:::

::::

::::{grid}
:gutter: 2

:::{grid-item-card}
```{image} img/logo_opencv.png
:width: 360px
:align: left
```
[OpenCV](https://github.com/opencv/opencv-python) propose des algorithmes pour les applications de vision comme identifier des objets, classer des actions humaines dans des vidéos, suivre des objets en mouvement, extraire des modèles 3D d'objets, suivre les mouvements oculaires...
:::

:::{grid-item-card}
```{image} img/logo_graphviz_with_text.png
:width: 360px
:align: left
```
[Graphviz](https://anaconda.org/anaconda/graphviz) permet de dessiner automatiquement des graphes orientés ou non, définis uniquement par leurs noeuds et les arcs. Le placement de noeud et le tracé des arcs sont obtenus par des algorithmes d'optimisation.
:::

:::{grid-item-card}
```{image} img/logo_networkx.png
:width: 360px
:align: left
```
<br />[NetworkX](https://networkx.org/) permet la création, la manipulation et l'analyse des graphes et des réseaux en proposant des algorithmes de parcours de graphe, de coloration de graphe, de flux de données, génération aléatoire de graphe...
:::

::::

On peut également citer :
- [SymPy](https://www.sympy.org) est une bibliothèque Python pour les mathématiques symboliques qui permet de faire du calcul arithmétique formel basique, de l'algèbre, des mathématiques différentielles, de la physique, de la mécanique classique ou quantique.




<!--


### Essais 

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

fence {code-block} python

```{code-block} python-console
>>> a = 'foo'
>>> print(a)
foo
>>> 1 / 0
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ZeroDivisionError: integer division or modulo by zer
```

```{note} En bref
- Le langage Python est un langage interpréter
- Un interpreteur Python est l'application qui exécute le code source instruction par instruction
```

-->