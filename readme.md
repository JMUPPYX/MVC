## Model View Controller:


Le MVC :
- sépare les responsabilités,
- adapté au travail collaboratif entre développeurs et permet une gestion plus claire du code.
- c'est un outil puissant pour concevoir des applications robustes et bien organisées.

C'est un système de communication entre trois entités :
- Model
- View
- Controller

![capture d'ecran](/img/MVC.png)

C'est trois entités communiquent par des événements, la POO entre autre.

La view (html) c'est l'interface homme/machine (page web,application)

Le model contient les données c'est le coeur de l'application.(Base de données)

Le controller  est un intermédiaire qui gère les actions de l'utilisateur et les interactions entre la vue et le modèle. Il contrôle les données.
Lors d'une action, il envoit un évenement au model qui peut être ajouter/modifier/supprimer pour modifier son état.

![capture d'ecran](/img/images.png)

Exemple :

Ne pas oublier la connexion avec PDO si vous souhaitez effectuer un test...

Modél : 

On crée un classe pour représenter une entité de notre application avec des proriétés vide.
````php
// Film.php
class Film {
    public $id;
    public $titre;
    public $realisateur;
    public $anneeSortie;
    // Autres propriétés spécifiques à un film

    public function __construct($id, $titre, $realisateur, $anneeSortie) {
        $this->id = $id;
        $this->titre = $titre;
        $this->realisateur = $realisateur;
        $this->anneeSortie = $anneeSortie;
    }
}
````

Vue : 

 Interface utilisateur :
````html
<!-- film_details.php -->
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Détails du film</title>
</head>
<body>
    <h1>Détails du film</h1>
    <p>Titre :<?php echo $film->titre; ?></p>
    <p>Réalisateur :<?php echo $film->realisateur; ?></p>
    <p>Année de sortie : <?php echo $film->anneeSortie; ?></p>
    <!-- Autres détails du film -->
</body>
</html>
````

Controller :

Gére les interactions entre le model et la vue il contrôle tout simplement.
On pourrait créer une classe controller avec des fonctions pour ajouter/modifier/supprimer des films.

````php
// FilmsController.php
class FilmsController {
    public function details($filmId) {
        // récuperation des données depuis le model (qui se connecte à la BDD)
        $film = new Film(1, "Inception", "Christopher Nolan", 2010);
        require_once 'film_details.php'; // Charge la vue
    }
    // Autres actions (Liste des films, Ajouter un film, etc.)
}

````

