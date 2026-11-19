# Session 07 - Défi : articles de la même catégorie

La section « Dans la même catégorie » apparaît sous un article publié qui a une catégorie : oui
L'article affiché n'apparaît pas dans sa propre section : oui
Un brouillon de la même catégorie n'apparaît pas : oui
La page s'ouvre sans LazyLoadingViolationException : oui
Le nouveau test passe et php artisan test est vert : oui

Combien de requêtes SQL charge la section, et pourquoi pas une par carte ?
La section charge 4 requêtes SQL (les articles de la catégorie, puis les auteurs, les catégories et les tags), quel que soit le nombre de cartes affichées, grâce au chargement anticipé avec with('user', 'category', 'tags'). Sans with(), chaque carte exécuterait ses propres requêtes (problème N+1), ce qui ajouterait 3 requêtes par carte (9 requêtes pour 3 cartes) et déclencherait une LazyLoadingViolationException.
