# TP n°4

Avec `cargo`, créez un nouveau projet nommé `tp4`.

Nous allons créer une application similaire à celle du TP3,
mais en tirant profit de ce que nous avons vu à cette séance.

## Le type `Point`

Dans un premier temps, on vous demande de créer un module `point`,
dans lequel vous définirez un type struct public `Point` représentant un point du plan,
dont les coordonées x et y sont des flottants sur 64 bits.

On vous demande ensuite d'écrire les **méthodes** publiques suivantes pour ce type :

* un constructeur `new` qui prend deux flottants x et y, et retourne le point correspondant ;
* `display` qui affiche à l'écran les coordonnées du point ;
* `distance` qui prend en paramètre un deuxième point, et retourne la distance entre self et l'autre point ;
* `middle` qui prend en paramètre un deuxième point, et retourne le milieu entre self et l'autre point ;
* `translate_h` qui prend en paramètre un flottant f, et modifie le point en le translatant horizontalement de la valeur f.

NB: vous pourrez bien sûr vous inspirer largement du type `Point` défini dans le TP précédent.

## Le type `Value`

On vous demande maintenant de créer un module `value`,
dans lequel vous définirez un type enum publique `Value` dont les variantes sont
`Number` (contenant un flottant), et `Point` (contenant un `Point` tel que défini ci-dessus).

On vous demande ensuite d'écrire les méthodes publiques suivantes pour ce type :

* `display` qui affiche à l'écran la valeur (flottant ou point).

## Pile de valeurs

On vous demande maintenant de créer un module `stack`,
qui servira à gérer une pile de valeurs gérée par un vecteur de `Value`.
Comme dans le TP précédent,
on utilisera les méthodes [`Vec::push`] et [`Vec::pop`]
pour ajouter et récupérer des valeurs dans la pile.

On vous demande d'écrire les fonctions suivantes, qui prennent toutes en paramètre un vecteur de points :

* `display_stack` qui affiches toutes les valeurs de la pile à l'écran ;
* `make_point` qui vérifie que les deux valeurs au sommet de la pile sont bien des nombres,
  et les remplace par un point construit à partir de ces deux valeurs ;
* `compute_distance` qui vérifie que les deux valeurs au sommet de la pile sont bien des points,
  et les remplace par leur distance ;
* `compute_middle` qui vérifie que les deux valeurs au sommet de la pile sont bien des points,
  et les remplace par leur milieu ;
* `translate_h` qui vérifie que les deux valeurs au sommet de la pile sont bien un point et un nombre,
  retire le nombre, et translate horizontalement le point de la valeur de ce nombre.
  
Pour toutes ces méthodes, si la pile ne contient pas le bon nombre d'éléments, ou s'ils ne sont pas du bon type (nombre ou point), un message d'erreur est affiché et le contenu de la pile n'est pas modifié.

## Interface en ligne de commande

Écrivez maintenant la fonction `main` qui permette de gérer interactivement une pile de valeurs telle que décrite ci-dessus.
Votre programme lira répétitivement des commandes sur son entrée standard :

* `!` ou `quit` interromp le programme ;
* tout nombre ajoutera ce nombre au sommet de la pile ;
* `p` ou `point` appellera la fonction `make_point` ;
* `d` ou `distance` appellera la fonction `compute_distance` ;
* `m` ou `middle` appellera la fonction `compute_middle` ;
* `h` ou `translate_h` appellera la fonction `translate_h` ;
* une ligne vide de fait rien ;
* tout autre texte saisi affiche un message d'erreur.

Après chaque commande,
le programme affichera le contenu de la pile et attendra la prochaine commande.

### Indications

* Pour calculez une distance, notez que toute valeur `f64` a une méthode `sqrt`
  qui donne sa racine carrée.
  
* Pour accéder depuis un module à un autre module du programme,
  préfixez le nom de ce module par `crate` (e.g. `use crate::point::Point` depuis le module `value`).
  
[`Vec::push`]: https://doc.rust-lang.org/std/vec/struct.Vec.html#method.push
[`Vec::pop`]: https://doc.rust-lang.org/std/vec/struct.Vec.html#method.pop


