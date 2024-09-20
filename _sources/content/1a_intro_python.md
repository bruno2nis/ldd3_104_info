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
Un **code source** en langage Python est un texte qui décrit un ensemble d'**instructions** écrites selon des règles de **syntaxe** et qui produisent des actions conformément à leur **sémantique** grâce à l'**interpréteur Python**. Le code source peut également contenir des commentaires.
```




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


-->