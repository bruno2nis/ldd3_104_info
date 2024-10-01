# Projet

Support du projet :
- les graphes orienté et la recherche de chemin 

Compétence à développer
- programmation orienté objet (à partir d'un modélisation déjà ébauché, et d'une interface)
- codage d'algorithmes déjà établis (parcours de graphe en largeur, recherche du chemin le plus cours)
- création d'un fichier contenant les résultats formaté
- lecture d'un fichier de donnée format


```{mermaid}
classDiagram
    Arc "*" -- "1" Sommet: destination
    Arc "*" -- "1" Sommet: source
    Graphe "1" -- "*" Arc
    Graphe "1" -- "*" Sommet

    class Graphe{
        nom: int
        ajouter_sommet(nom: str) : None
        ajouter_arc(nom_dep: str, nom_arr: ste, poids: int) : None
    }

    class Arc{
        poids: int
    }

    class Sommet{
        nom : str
    }

```
