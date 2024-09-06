# LDD3_104_info

- e-campus https://ecampus.paris-saclay.fr/course/view.php?id=39705
- [Pages html](https://ldd3-104-info-bruno-denis-dc8b9a8fbd3a9c0c0f23ecf551f8642b0b3e7.gitlab.dsi.universite-paris-saclay.fr/) sur le gitlab de l'université https://ldd3-104-info-bruno-denis-dc8b9a8fbd3a9c0c0f23ecf551f8642b0b3e7.gitlab.dsi.universite-paris-saclay.fr/
- [Pages html](https://bruno2nis.github.io/ldd3_104_info) sur github https://bruno2nis.github.io/ldd3_104_info<br />
  Ajouter le fichier `.nojekyll` à la racine pour que les CSS soit pris en compte

Procédure de mise en ligne
- **éditer** les fichier dans ./content et en particulier les carnet `Xk_BE_solution.ipynb`
- **générer les carnets** ; exécuter depuis ./content la commande `python .\scripts\base64_converter.py` pour générer le carnet avec les images embarquées et les solutions `./Xk_be_solution_embed.ipynb` pour les collègue et le carnet avec les images embarquée sans les solutions `./1k_be_embed.ipynb` pour les étudiants
- **générer le site** en local avec la commande `jupyter book build .\ldd3_104_info\`
- **copier le site dans le dépôt git local** ./web/ldd3_104_info avec `SyncBackFree`
- **pousser le site sur le déôt distant** avec par exemple github desktop
- **téléverser les carnets** sur e-campus (la version collège et le version étudiant)

