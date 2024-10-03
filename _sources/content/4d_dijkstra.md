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

# Algorithme de Dijkstra

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
