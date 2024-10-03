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

# Modélisation orientée objet

Un [diagramme de classes](https://fr.wikipedia.org/wiki/Diagramme_de_classes) est un outil de modélisation utilisé en génie logiciel pour représenter la structure d'un système orienté objet. Il fait partie des langages de modélisation [UML](https://fr.wikipedia.org/wiki/UML_(informatique)) (Unified Modeling Language) du génie logiciel et du langage de modélisation [SysML](https://fr.wikipedia.org/wiki/Systems_Modeling_Language) (Systems Modeling Language) de l'ingénierie système. Il permet de visualiser les classes, leurs attributs, leurs méthodes, ainsi que les relations entre elles. Un diagramme de classe permet :
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

Le diagramme ci-dessous présente une relation entre les classes `NomClasse1` et `NomClasse1`. Les annotations sur le lien permettent de décrire la relation.
- `relation` placée au milieu de la ligne de relation décrit la nature de la relation entre les classes
- `1` et `*` placées aux extrémités des lignes de relation sont des indications de multiplicité qui répondent aux questions "comment d'instances d'une classe peuvent être associées à une instance d'une autre classe ?".
  - ici `*` indique qu'une instance de `NomClasse1` est associée à plusieurs instances de `NomClasse2`
  - ici `1` indique qu'exactement une instance de `NomClasse2` est associée à plusieurs instances de `NomClasse1`

```{mermaid}
classDiagram
    direction LR
    NomClasse1 "1" -- "*" NomClasse2: relation
```

Le diagramme de classe UML suivant présente un modèle des graphes orientés et pondérés. Ici les méthodes ne sont pas encore détaillées. Ce diagramme explique qu'un Graphe contient plusieurs Sommets et plusieurs Arcs, et qu'un Arc est en relation avec exactement un Sommet source et un Sommet destination.

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

Le diagramme suivant fait apparaitre les méthodes associées à la classe Graphe qui sont attendue du projet. Chacun et chacune sera libre d'ajouter les méthodes supplémentaires qui lui sembleront utiles. 

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
        ajouter_arc(nom_dep: str, nom_arr: ste, poids: int): None
        changer_nom(nom: str): None
        rapport_textuel(): str
        rapport_html(): None
        initialiser_avec_dict(donnee: dict): None
        initialiser_avec_fichier(nom_fichier: str): None
        sauver_dans_fichier(nom_fichier: str): None
        dijkstra(nom_sommet_depart: str): arbre
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