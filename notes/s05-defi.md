# Session 05 - Défi : articles récents sur l'accueil

latestPosts contient au plus 3 articles : oui
Seuls les articles publiés sont transmis à la vue : oui
home.blade.php utilise x-post-card et @forelse : oui
Le nouveau test passe et php artisan test est vert : oui

Pourquoi get() et pas paginate(3) sur la page d'accueil ?
La page d'accueil affiche uniquement un aperçu fixe des trois derniers articles publiés sans pagination ni boutons « Suivant / Précédent ». L'appel à get() exécute la requête et renvoie une collection contenant au plus 3 éléments grâce à take(3), ce qui est léger et adapté à une page d'accueil, alors que paginate(3) est conçu pour naviguer sur l'ensemble des pages d'une ressource (comme sur /posts).
