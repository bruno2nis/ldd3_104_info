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

# Bibliothèques

Comme tous les langages informatiques, le langage Python offre un nombre limité de fonctionnalités essentielles. Les bibliothèques sont là pour apporter de nouvelles fonctionnalités plus riches et d'un usage courant. 

## Bibliothèque standard Python

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

## Bibliothèques tierces

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


