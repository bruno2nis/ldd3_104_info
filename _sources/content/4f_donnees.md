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

# Jeu de données 

## Graphe de démonstration

<img src="img/PRO_digraphe_demo_01.png" style="width:350px" width="400px" /><br />

Contenu du fichier graphe_demo.json représentant le graphe de démonstration au format texte JSON

```{code-block} json
{
    "nom": "graphe_demo",
    "sommets": ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J"],
    "arcs": [
        ["A", "A", 2],
        ["A", "B", 5],
        ["A", "C", 8],
        ["B", "C", 6],
        ["B", "D", 8],
        ["B", "E", 6],
        ["C", "B", 2],
        ["C", "D", 1],
        ["C", "E", 2],
        ["D", "E", 3],
        ["D", "F", 1],
        ["E", "A", 5],
        ["E", "D", 1],
        ["E", "G", 5],
        ["F", "D", 4],
        ["F", "E", 1],
        ["F", "G", 3],
        ["F", "H", 6],
        ["E", "I", 3],
        ["G", "H", 2],
        ["H", "B", 6],
        ["H", "B", 7],
        ["I", "J", 4],
        ["J", "I", 5]
    ]
}
```

Dictionnaire Python assigné à `donnees` et représentant le graphe de démonstration

```{code-block} python
donnees = {
    "nom": "graphe_demo",
    "sommets": ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J"],
    "arcs": [
        ("A", "A", 2),
        ("A", "B", 5),
        ("A", "C", 8),
        ("B", "C", 6),
        ("B", "D", 8),
        ("B", "E", 6),
        ("C", "B", 2),
        ("C", "D", 1),
        ("C", "E", 2),
        ("D", "E", 3),
        ("D", "F", 1),
        ("E", "A", 5),
        ("E", "D", 1),
        ("E", "G", 5),
        ("F", "D", 4),
        ("F", "E", 1),
        ("F", "G", 3),
        ("F", "H", 6),
        ("E", "I", 3),
        ("G", "H", 2),
        ("H", "B", 6),
        ("H", "B", 7),
        ("I", "J", 4),
        ("J", "I", 5),
    ],
}
```