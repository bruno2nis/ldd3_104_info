# Ecosystème Python

- Python est un langage de programmation
- Les instructions du langage Python sont lues, interprétées et exécutées par un interpréteur Python
- L'interpréteur Python peut être utilisé soit :
    * en mode interactif, les intructions sont saisies depuis une invite de commande (`>>>` ou `In [1]:`)
    * en mode script, les instructions sont lues depuis un fichier source (extension `.py`)

![Interpréteur Python](img/python_interpreteur.svg)


L'interpréteur Python transforme les instructions d'entrées en `bytecodes` indépendant de la machine cible, puis exécute les bytecodes avec une machine virtuelle.

![Interpréteur Python](img/python_interpreteur_detail.svg)

Quelques implémentations de l'interpréteur Python :
- **CPython** (l'implémentation de référence open source en langage C), `python.exe` sous Windows, `python3` sous Linux et MacOS, 
- **IPython**, des fonctionnalités avancées en mode interactif (coloration syntaxique, complétion de code, magic commands, visualisation des données) et une intégration simplifiée, `ipython.exe` sous Windows, `ipython` sous Linux et MacOS. 
- **MicroPython**, pour des plateformes à très faibles ressources matérielles comme les microcontrôleurs

Pour éditer les programmes, les exécuter et les mettre au point, les environnements de développement intégrés (IDE, Integrated Development Environment) fournissent de nombreuses fonctionnalités, comme par exemple **Spyder** (exemple de [tutoriel sur koor.fr](https://koor.fr/Python/Tutorial/python_ide_spyder.wp))

![Écran de l'IDE Spyder](img/spyder.svg)


Python est accompagné d'une bibliothèque standard de plus de 100 modules logiciels. 

Il existe de nombreux modules tiers, parmi les plus utilisés pour le calcul scientifique on peut citer **NumPy** (algèbre linéaire), **SciPy** (programmation scientifique), **Matplotlib** (visualisation des données), **Scikit Learn** et **TensorFlow** (apprentissage automatique) ou **Graphviz** (visualisation de graphes).

![logo des modules Python](img/logo_modules.svg)

Ces modules sont souvent développés en utilisant d'autres modules existants, il est donc important que les versions des modules soient compatibles entre elles. Pour cela, il existe des gestionnaires de paquets de modules et d'environnement comme par exemple **conda**

![logo Conda](img/logo_Conda.svg)



Finalement pour travailler en toute séréinité avec Python il faut :
- un interpréteur Python avec ses modules logiciel standard (ex : CPython, IPython),
- un environnement de développement intégré (ex : Spyder),
- un ensemble de bibliothèques de modules logiciels tiers (ex : numpy, matplotlib, graphiz),
- un gestionnaire de paquets de modules (ex : conda)
- un gestionnaire d'environnement d'exécution (ex : conda)

Il existe des **distributions** logicielles qui incluent l'ensemble de ces fonctionnalités, par exemple, la distribution open source **Anaconda** ([site officiel](https://www.anaconda.com/products/distribution))

![Logo Anaconda](img/logo_Anaconda.svg)

<font color="#a22631">

Anaconda navigator fournit une interface graphique pour utiliser et gérer de la distribution Python. Ci-dessous, la page d'accueil avec le bouton de lancement de **Spyder**

![Navigateur Anaconda - Acceuil](img/anaconda_navigateur_accueil.svg)

Anaconda navigator fournit également une interface graphique pour la de gestion des **paquets logiciels** (installation, mise à jour, suppression) et de gestion des environnements d'exécution (create, clone, remove...) permettant de grouper et d'isoler dans un conteneur une version de Python avec des versions spécifiques de chaque paquet logiciel. 

![Navigateur Anaconda - Environnement](img/anaconda_navigateur_environnement.svg)

Pour l'UE LDD3 104 Informatique, nous utiliserons
- la distribution Anaconda à télécharger depuis https://www.anaconda.com/products/distribution (choisir la version Python 3.X)
- l'IDE spyder (inclus dans la distribution Anaconda)
- la bibliothèque standard (incluses dans la distribution Anaconda)
- les paquets logiciels tiers ([Tuto en anglais](https://docs.anaconda.com/anaconda/navigator/tutorials/manage-packages/#installing-a-package) pour les installer avec Anaconca navigator, il sera peut être nécessaire de l'exécuter en mode administrateur)
    * `python-graphviz` (inclus dans Anaconda, mais pas installé par défaut)
    * `pyparsing` (généralement installé par defaut dans Anaconda)
