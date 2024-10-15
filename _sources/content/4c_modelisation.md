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
        ajouter_arc(nom_source: str, nom_dest: str, poids: int): None
        changer_nom(nom: str): None
        rapport_textuel(): str
        rapport_html(): str
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


<!--  
## API d'un Graphe

### Attributs

#### `nom` 

### Méthodes


#### `ajouter_sommet()`

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

-->