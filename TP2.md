# TP n°2

Avec `cargo`, créez un nouveau projet nommé `tp2`.

## Le type `Point`

Dans un premier temps, on vous demande de créer un type `Point` représentant un point du plan,
dont les coordonées x et y sont des flottants sur 64 bits.

On vous demande ensuite d'écrire les fonctions suivantes :

* `display_point` qui prend en paramètre un point, et affiche ses coordonnées à l'écran ;
* `middle` qui prend en paramètres deux points, et retourne un nouveau point correspondant à leur milieu ;
* `translate_h` qui prend en paramètre un point p et un flottant f, et modifie p en le translatant horizontalement de la valeur f.

NB: il vous revient de choisir judicieusement le mode de passage de paramètre : par valeur (*move*), par référence (*borrow*), ou par référence mutable (*mutable borrow*).

## Pile de points

On va ensuite écrire des fonctions qui prennent en paramètre un vecteur de points,
géré comme un pile (dernier entré, premier sorti) à l'aide des méthodes [`Vec::push`] et [`Vec::pop`].

On vous demande d'écrire les fonctions suivantes :

* `display_stack` qui prend en paramètre un vecteur de points, et les affiches tous à l'écran ;
* `compute_middle` qui prend en paramètre un vecteur de points de longueur ≥ 2, et remplace les deux derniers points du vecteur par leur milieu.

## Interface en ligne de commande

Écrivez maintenant la fonction `main` qui permette de gérer interactivement une pile de points telle que décrite ci-dessus.
Votre programme lira répétitivement des commandes sur son entrée standard :

* `!` ou `quit` interromp le programme ;
* `p` ou `point` entraine la lecture deux nombres x et y au clavier, et ajoute le point correspondant dans la pile ;
* `m` ou `middle` remplace les deux points du dessus de la pile par leur milieu ;
* une ligne vide de fait rien ;
* tout autre texte saisi affiche un message d'erreur.

Après chaque commande,
le programme affichera le contenu de la pile et attendra la prochaine commande.

Indications:

* Pour afficher un message d'erreur, on utilisera `eprinln!` au lieu de `prinln!`
  (affichage sur l'erreur standard).
  
* Pour lire une ligne au clavier, vous devrez :

    + préparer une chaîne de caractère mutable `buffer`,
    + utiliser la commande `std::io::stdin().read_line(&mut buffer).unwrap();`
      qui attend une saisie au clavier, et ajoute le texte lu à la chaîne `buffer`, et
    + penser à vider la chaîne entre deux lectures, par exemple avec la méthode [`String::clear`].

* Pour convertir une chaîne `txt` en `f64`, vous devez écrire `txt.parse().unwrap()`.

[`Vec::push`]: https://doc.rust-lang.org/std/vec/struct.Vec.html#method.push
[`Vec::pop`]: https://doc.rust-lang.org/std/vec/struct.Vec.html#method.pop
[`String::clear`]: https://doc.rust-lang.org/std/vec/struct.Vec.html?search=String%3A%3Aclear


