# Session 08 - Défi

La route posts.tag utilise {tag:slug} : oui
La page d'un tag n'affiche ni brouillon ni article d'un autre tag : oui
Les tags des cartes sont des liens : oui
L'accueil n'affiche que les tags qui ont au moins un article publié : oui
Les trois nouveaux tests passent et php artisan test est vert : oui

Pourquoi filtrer les tags vides après get() plutôt que d'afficher (0) ?
Sur l'accueil, un tag sans aucun article publié n'a pas d'intérêt pour le visiteur : cliquer dessus mènerait à une page vide. Le filtrage après get() (ou via une clause SQL) permet de n'afficher que les tags utiles ayant du contenu accessible.

Combien de requêtes ajoute la liste des tags populaires, et pourquoi pas une par tag ?
Elle n'ajoute qu'une seule requête SQL grâce à `withCount(['posts' => ...])` qui agrège le nombre d'articles publiés directement dans la requête principale (via un sous-select), évitant ainsi le problème N+1.

Pourquoi aucune migration, aucun modèle et aucun test n'a changé ?
Parce qu'Eloquent et le Query Builder de Laravel constituent une couche d'abstraction (ORM) indépendante du système de gestion de base de données sous-jacent (SQLite, PostgreSQL, MySQL). Le même code s'adapte automatiquement sans modifier les modèles, les migrations ou les tests.
