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

# Modélisation

## Graphes

### Définitions

Un **graphe** est un couple $G = (V, E)$ comprenant deux ensembles :
- $V$ un ensemble de sommets (*vertices* en anglais)
- $E$ un ensemble d'arêtes (*edges* en anglais), chacune étant une paire de sommets $\{u, v\}$ avec $u$, $v \in V$

Un **graphe orienté** est un graphe pour lequel les arêtes sont des couples $(u, v) \in V \times V$. Les arêtes d'un graphe orienté sont souvent appelées *arcs*. Les graphes orientés sont parfois appelés *digraph* par contraction de l'anglais *directed graph*

Un **graphe pondéré** (ou valué) est un graphe pour lequel un nombre positif est associé à chaque arête. Un graphe pondéré est un triplet $G = (V, E, w)$ où $V$ est l'ensemble de sommets, $E$ est l'ensemble des arêtes et $w : E \rightarrow \mathbb{R}_+$ est la fonction de pondération. $w(e)$ est appelé *poids* de l'arête $e \in E$.

Un **multigraphe** est un graphe où $E$ est un [multiensemble](https://fr.wikipedia.org/wiki/Multiensemble) (parfois appelé *sac*), c'est-à-dire une sorte d'ensemble dans lequel chaque élément peut apparaitre plusieurs fois. Un multigraphe autorise plusieurs arêtes entre deux sommets identiques.

Un **arbre** est un graphe sans circuit (suite d'arcs consécutifs dont les deux sommets extrémités sont identiques) et connexe (d'un seul tenant) dont la forme évoque la ramification des branches d'un arbre.

Exemple de représentation graphique des graphe :

::::{grid}

:::{grid-item-card} Graphe

```{image} img/PRO_graphe_exemple_01.png
:alt: Graphe
:align: center
:width: 120px
```
:::

:::{grid-item-card} Graphe orienté

```{image} img/PRO_graphe_exemple_02.png
:alt: Graphe orienté
:align: center
:width: 120px
```

Les arêtes sont des arcs orientés
:::

:::{grid-item-card} Graphe pondéré

```{image} img/PRO_graphe_exemple_03.png
:alt: Graphe pondéré
:align: center
:width: 120px
```

Un poids est associé au arêtes
:::

:::{grid-item-card} Multigraphe

```{image} img/PRO_graphe_exemple_04.png
:alt: Multigraphe
:align: center
:width: 120px
```

Plusieurs arêtes peuvent relier une paire de sommets
:::

:::{grid-item-card} Arbre

```{image} img/PRO_graphe_exemple_05.png
:alt: Graphe pondéré
:align: center
:width: 120px
```

Graphe connexe sans circuit
:::

::::

### Exemples d'utilisations
 
Un multigraphe orienté et pondéré est un outil de modélisation et d'analyse très répandu dans les sciences de l'ingénieur.
- ordonnancement de projet (diagramme de PERT)
- système de transport routier, ferroviaire, ou aérien
- système de distribution (eau potable, énergie électrique, hydraulique, pneumatique, géothermique ...)
- structure mécanique en treillis (ouvrage d'art, impression 3D, ...)
- système polyarticulé (cinématique ...)
- automate à états finis (automatisation des systèmes) 
- réseau électrique (lois de Kirchhoff)
- routage des circuits intégrés
- réseau de communication 


## Modélisation orientée objet

### Diagramme de classes

Un [diagramme de classes](https://fr.wikipedia.org/wiki/Diagramme_de_classes) est un outil de modélisation utilisé en génie logiciel et en ingénierie système pour représenter la structure d'un système orienté objet. Il fait partie des langages de modélisation [UML](https://fr.wikipedia.org/wiki/UML_(informatique)) (Unified Modeling Language) du génie logiciel et du langage de modélisation [SysML](https://fr.wikipedia.org/wiki/Systems_Modeling_Language) (Systems Modeling Language) de l'ingénierie système. Il permet de visualiser les classes, leurs attributs, leurs méthodes, ainsi que les relations entre elles. Un diagramme de classe permet :
- la visualisation de la structure du système
- l'identification des relations pour comprendre comment les classes collaborent 
- la communication entre les membres d'une équipe de développement
- la planification du codage facilitant la répartition du codage entre les développeurs et les développeuses
- la documentation du projet

Le diagramme ci-dessous montre la représentation d'une classe nommée `NomClasse` avec la zone où les attributs sont listés et celle où les méthodes apparaissent.

```{mermaid}
classDiagram
    class NomClasse{
        attributs
        méthodes()
    }
```
<br />

Le diagramme ci-dessous présente une relation entre les classes `NomClasse1` et `NomClasse2`. Les annotations sur le lien permettent de décrire la relation.
- `relation`, placée au milieu de la ligne de relation, décrit la nature de la relation entre les classes
- `1` et `*`, placées aux extrémités des lignes de relation, sont des indications de multiplicité qui répondent à la question «&nbsp;combien d'instances d'une classe peuvent être associées à une instance d'une autre classe&nbsp;?&nbsp;».
  - ici `*` indique qu'une instance de la classe `NomClasse1` est en relation avec plusieurs instances de  le classe `NomClasse2`
  - ici `1` indique qu'une instance de la classe `NomClasse2` est en relation avec exactement une instances de la classe `NomClasse1`

```{mermaid}
classDiagram
    direction LR
    NomClasse1 "1" -- "*" NomClasse2: relation
```

### Modélisation objet d'un graphe

Le diagramme de classe UML suivant présente un modèle des graphes orientés et pondérés. Ici, les méthodes ne sont pas encore détaillées. 

```{mermaid}
classDiagram
    direction LR
    
    class Graphe{
        nom: str
    }

    class Arc{
        poids: int
    }

    class Sommet{
        nom: str
    }

    Graphe "1" -- "*" Arc: contient
    Graphe "1" -- "*" Sommet: contient
    Arc "*" -- "1" Sommet: source
    Arc "*" -- "1" Sommet: destination
```
<br />

Ce diagramme explique qu'une instance de la classe Graphe est en relation avec plusieurs instances de la classe Sommet et plusieurs instances de la classe Arcs, et qu'une instance de la classe Arc est en relation, nommée source, avec exactement une instance de la classe Sommet et qu'une instance de la classe Sommet destination.


Le diagramme suivant fait apparaitre les méthodes associées à la classe Graphe qui sont attendues du projet. Chacun et chacune sera libre d'ajouter les méthodes supplémentaires qui lui sembleront utiles. Pour les futurs utilisateurs et utilisatrices de votre code, l'interface de programmation (API pour *Application Programming Interface* en anglais) est celle de la classe Graphe. Cela signifie que les méthodes de la classe Graphe doivent être scrupuleusement respectées et servent de cahier de charge au projet.

```{mermaid}
classDiagram
    direction LR
    Graphe "1" -- "*" Arc: contient
    Graphe "1" -- "*" Sommet: contient
    Arc "*" -- "1" Sommet: destination
    Arc "*" -- "1" Sommet: source

    class Graphe{
        nom: str
        ajouter_sommet(nom: str): None
        ajouter_arc(nom_dep: str, nom_arr: str, poids: int): None
        changer_nom(nom: str): None
        rapport_textuel(): str
        rapport_html(): None
        initialiser_avec_dict(donnee: dict): None
        initialiser_avec_fichier(nom_fichier: str): None
        sauver_dans_fichier(nom_fichier: str): None
        dijkstra(nom_sommet_depart: str): Graphe
        __str__(): str
        __repr__(): str
    }

    class Arc{
        poids: int
    }

    class Sommet{
        nom : str
    }
```

#### `__str__()` 

La méthode renvoie une chaine de caractère qui décrit une instance de Graphe, elle est de la forme `<Graphe: NNNN, SS sommets, AA arcs>` où
- `NNNN` est l'attribut "nom" de l'instance de Graphe
- `SS` est le nombre d'instances de Sommet en relation avec l'instance de Graphe
- `AA` est le nombre d'instances d'Arc en relation avec l'instance de Graphe

Exemple: 
- `<Graphe: mon_graphe, 6 sommets, 14 arcs>`

#### `__repr()__`

La méthode renvoie la chaine de caractère officielle d'une instance de Graphe, elle est de la forme `Graphe(SS sommets, AA arcs)` où
- `SS` est le nombre d'instances de Sommet en relation avec l'instance de Graphe
- `AA` est le nombre d'instances d'Arc en relation avec l'instance de Graphe

Exemple
- `Graphe(6 sommets, 14 arcs)`


## Algorithme de Dijkstra

L'algorithme de Dijkstra résout le problème du plus court chemin dans un graphe. Plus précisément, il calcule les plus courts chemins à partir d'un sommet de départ vers tous les autres sommets dans un graphe orienté pondéré par des réels positifs. Le résultat d'algorithme est un arbre (graphe orienté particulier) dont la racine est le sommet de départ et dans lequel un chemin unique, le plus court, relie deux sommets. Chaque sommet est associé à la plus courte distance qui le sépare du sommet de départ.


<img src="img/dijkstra_algo_entrees_sorties.png" style="width:300px" with="300px"/><br />

Description de l'algorithme issue de la page ["Algorithme de Dijkstra"](https://fr.wikipedia.org/wiki/Algorithme_de_Dijkstra) de Wikipédia.

<div style="background-color:rgba(0, 0, 0, 0.0470588); padding:10px 0; font-family:monospace; font-size:0.8em;">
<strong>Entrées :</strong> <br>
    &nbsp;&nbsp;- <font color = "green">G</font> = (<font color = "green">S</font>, <font color = "green">A</font>) un graphe avec une pondération positive <font color = "blue">poids</font> des arcs<br>
    &nbsp;&nbsp;- <font color = "green">S<sub>deb</sub></font> un sommet de <font color = "green">S</font><br>

<strong>Sorties :</strong> <br>
    &nbsp;&nbsp;- <font color = "green">P</font> = (<font color = "green">S</font>, <font color = "green">Af</font>) un graphe (arbre de sommet Sdeb) <br>
    &nbsp;&nbsp;&nbsp;&nbsp;avec une pondération positive <font color = "blue">d</font> (distance) des sommets<br><br>

    
P := <font color = "orange" over>⌀</font><br>
    <font color = "blue">d</font>[<font color = "green">a</font>] := <font color = "orange" over>+∞</font> <strong>pour</strong> chaque sommet <font color = "green">a</font><br>
    <font color = "blue">d</font>[<font color = "green">s<sub>deb</sub></font>] := <font color = "orange" over>0</font><br>
    <strong>Tant qu</strong>'il existe un sommet hors de <font color = "green">P</font><br>
    &nbsp;&nbsp;&nbsp;&nbsp;Choisir un sommet <font color = "green">a</font> hors de <font color = "green">P</font> de plus petite distance <font color = "blue">d</font>[<font color = "green">a</font>]<br>
    &nbsp;&nbsp;&nbsp;&nbsp;Mettre <font color = "green">a</font> dans <font color = "green">P</font><br>
    &nbsp;&nbsp;&nbsp;&nbsp;<strong>Pour</strong> chaque sommet <font color = "green">b</font> hors de <font color = "green">P</font> voisin de <font color = "green">a</font><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Si <font color = "blue">d</font>[<font color = "green">b</font>] > <font color = "blue">d</font>[<font color = "green">a</font>] + <font color = "blue">poids</font>(<font color = "green">a</font>, <font color = "green">b</font>)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">d</font>[<font color = "green">b</font>] := <font color = "blue">d</font>[<font color = "green">a</font>] + <font color = "blue">poids</font>(<font color = "green">a</font>, <font color = "green">b</font>)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color = "blue">prédécesseur</font>[<font color = "green">b</font>] := <font color = "green">a</font><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<strong>Fin Si</strong><br>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>Fin Pour</strong><br>
<strong>Fin Tant que</strong>
</div>
