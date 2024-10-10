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

# Présentation

## Support du projet

Le projet est articulé autour des graphes orientés et de la recherche de chemins, en particulier la recherche du chemin le plus long parmi les chemins les plus courts entre deux sommets. La {numref}`graphe_exemple` montre un de ces graphes où le plus court chemin pour aller du somment A au sommet E est mis en évidence en rouge.

```{figure} img/PRO_digraphe_exemple_02.png
:width: 250px
:name: graphe_exemple

Réprésentation graphique d'un graphe orienté pondéré
```

## Compétences développées

- Programmation orientée objet (à partir d'une modélisation déjà ébauchée, et d'une interface partiellement imposée)
- Codage d'algorithmes déjà établis (parcours de graphe en largeur, recherche du chemin le plus court)
- Lecture et création de fichiers contenant des données formatées

## Documents fournis

Les document sont disponibles sur le site [https://ecampus.paris-saclay.fr/](https://ecampus.paris-saclay.fr/course/view.php?id=39705)
- un carnet Jupyter `ldd3_104_projet.ipynb` avec les consignes séances par séances
- un graphe de démonstration sous la forme d'un dictionnaire Python et d'un fichier au format JSON `graphe_demo.json`
- un exemple de rapport sur le graphe de démonstration

## Travail demandé

Construire un code Python et un carnet Jupyter qui permettent 
- de construire un graphe
  - de manière interactive
  - depuis des données structurées dans un dictionnaire
  - depuis des données structurées dans un fichier
- de sauver un graphe dans un fichier au format JSON
- d'analyser le plus court chemin entre tous les couples de sommets d'un graphe, 
- d'identifier le plus long des plus courts chemins dans un graphe
- de construire un rapport textuel (texte brut)
- de construire un rapport au format HTML incluant une représentation graphique des graphes (copie d'écran {numref}`rapport_html`)

```{figure} img/PRO_rapport_html.png
:name: rapport_html

Copie d'écran d'un rapport au format HTML tel qu'il apparait dans un navigateur web.
```

## Résultats attendus (livrables)

Une archive au format ZIP, nommée `NOM_Prenom.zip` et déposée sur le site e-campus.
- l'archive doit contenir obligatoirement
  - un carnet Jupyter traitant le graphe de démonstration (création d'un objet de la classe Graphe, chargement des données depuis  fichier, ...) qui doit s'exécuter correctement sur le server JupyterHub
  - le fichier au format JSON décrivant le graphe de démonstration
- l'archive peut éventuellement contenir
  - un fichier de code Python (un module), si vous avez décidé d'externaliser une partie de votre code du carnet Jupyter 
  - tout autre fichier annexe utile à votre carnet Jupyter

``` none
NOM_Prenom.zip/            ┐
├── mon_carnet.ipynb       │  Partie obligatoire
├── graphe_demo.json       │
│                          ┘
├── mon_module.py          ┐
├── ...                    │  Partie optionnelle
```
