# LDD3 Informatique

Ce document est le support du module *informatique* (bloc outils numériques) de la Licence Double-Diplôme [LLD3 Sciences pour l'ingénieur](https://www.universite-paris-saclay.fr/formation/licence-double-diplome/mathematiques-physique-et-sciences-pour-lingenieur/ldd3-sciences-pour-lingenieur) de l'Université Paris-Saclay. 

```{note}
Lien vers la page du module de formation sur le site [https://ecampus.paris-saclay.fr/](https://ecampus.paris-saclay.fr/course/view.php?id=39705)
```

La compétence la plus importante pour un informaticien est la résolution de problèmes. Il s'agit de la capacité à formuler des problèmes, à réfléchir de manière créative à des solutions et à exprimer une solution de manière claire et précise :
- pour concevoir des systèmes programmés, comme les mathématiciens, les informaticiens utilisent des langages formels
- pour construire des systèmes programmés, comme les ingénieurs, les informaticiens assemblent des objets en composants plus complexes
- pour prédire le comportement des systèmes programmés, comme les scientifiques, les informaticiens observent des systèmes complexes, formulent des hypothèses et testent leurs prédictions.

Les objectifs de ce module sont :
- présenter les concepts sous-jacents à la résolution de problème par un programme informatique,
- mettre en oeuvre les moyens offerts par le langage Python pour les résoudre.

## Organisation du module

- cours 3 x 2 heures
- bureau d'étude 3 x 2 heures
- projet encadré 4 x 4 heures

L'enchainement chronologique des activités est le suivant :

````{mermaid}
%%| fig-responsive: true
flowchart LR
    CM1 --> TD1
    TD1 --> CM2
    CM2 --> TD2
    TD2 --> CM3
    CM3 --> TD3
    TD3 --> Projet
````

%L'équipe

%| | Cours | TD | Projet |
%|----|:--:|:--:|:---:|
%| Bruno Denis | X | X | X |
%| Yoann Guilhem | | X | X |
%| David Eteviant | | X | X |
%| Clément Ecker | | X | X |
%| Emmanuel Herrmann | | X | X |

## Contenu

### Cours 

- Semaine 1 
    - Concepts théoriques et applicatifs
    - Langage Python
        - Structure d'un programme: ligne physique, ligne logique, instruction, liste d'instruction, instruction composée, module, paquetage.
        - types natifs 
        - instructions simples et composées
- Semaine 2
    - Langage Python
        - fonctions définies utilisateur : définition, argument ordonné, argument nommé, compactage/décompactage
        - cadre d'exécution, pile des cadres d'exécution, portée des variables (LEGB)
- Semaine 3
    - Langage Python
        - classes définies par l'utilisateur : définition, héritage, propriété, encapsulation, polymorphisme
    - Développer une application : modularité, débogage (pdb, …), test (unitest, …), gestion de version, documentation (générateur de doc), environnement d’exécution (conda, …), ide (Jupyter Lab, Spyder, Visual Studio Code)

### Travaux dirigés (6 heures)

Les travaux dirigés sont des BE de 2 heures (bureau d'études) devant ordinateur. Selon les groupes, le travail se ferait sur du matériel personnel en salles banalisées ou dans des salles équipées d'ordinateurs. Aucune installation spécifique n'est nécessaire.

**Quelle installation est nécessaire ?** Les seuls prérequis techniques sont :
- appareil (ordinateur, tablette...) avec
    - un accès à un compte utilisateur (différent selon les salles)
    - un accès à internet
    - un navigateur web, par exemple Firefox, Chrome, Egde, ou Safari.
- une identité numérique de l'*École Normale Supérieure Paris-Saclay*

**A quoi ressemblent les sujets ?** Ce sont des carnets Jupyter (fichier au format texte JSON) qui mélangent des savoirs, des énoncés d'exercice, des zones de saisie de code Python, des zones de résultats d'exécution, des zones de test des résultats. Les carnets sont structurés en partie, section et sous-section.
- Si le titre de section commence par "⚙️ Exercice", la section contient un énoncé à traiter, sinon elle contient des connaissances à lire.
- Les titres contiennent une signalétique d'objectif à attendre, pour que chacun puisse adapter son travail en fonction de son niveau.
  - L'absence de carré coloré indique un contenu incontournable pour attendre l'objectif de la séance, les étudiants et étudiantes novices pourront s'y concentrer
  - 🟨 indique un contenu qui fait parti de l'objectif de l'ensemble du module, que les étudiants et étudiantes déjà familiers avec Python pourront aborder
  - 🟥🟥 indique un contenu qui sera utile pour la suite de la formation, les étudiants et les étudiantes à l'aise pourront y améliorer leurs compétences.


**Comment obtenir les sujets ?** Ils sont disponibles depuis la page e-campus du module de formation [lien](https://ecampus.paris-saclay.fr/course/view.php?id=39705). 


**Comment utiliser le sujet au format Jupyter?** voir section *JupyterLab - Instruction de démarrage* 
[doc](./9a_jupyterlab_instructions.md)


### Projet encadré (12 heures)



