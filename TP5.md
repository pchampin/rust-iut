# TP n°5

Créez un nouveau projet nommé `tp5` avec la ligne de commande `cargo new --lib tp5`.

Vous constaterez que le répertoire `src` ne contient pas de fichier `main.rs`,
mais un fichier `lib.rs`.
Ce projet ne sert pas à créer un fichier exécutable,
mais une bibliothèque réutilisable par d'autres.

## Tests unitaires

Pour tester le code de notre bibliothèque,
nous allons créer un module nommé `test` :

* créez un fichier `test.rs` dans le répertoire `src`;
* ajoutez à `lib.rs` la les lignes suivantes :
  ```rust
  #[cfg(test)]
  mod test;
  ```
  
NB: la directive #[cfg(test)] indique au compilateur que le module doit être compilé
*seulement* pour exécuter les tests unitaires.

Dans le fichier `test.rs`, ajoutez les lignes suivantes :
```rust
#[test]
fn test0() {
    assert!(1+1 == 3);
}
```

Notez que :
* la directive `#[test]` indique que cette fonction est un test unitaire ;
* la macro `assert!` panique si l'expression passée en paramètre est fausse.

Un test unitaire est considéré comme un succès s'il ne panique pas.

Pour lancer les tests, utilisez la commande `cargo test`,
et constatez que `test0` échoue.
Modifiez le code pour faire en sorte qu'il réussisse, et lancez `cargo test` à nouveau.


## Le type `Vecteur`

Votre travail consiste maintenant à définit un type `Vecteur`
représentant un vecteur dans un espace à deux dimensions.

Pour chacune des méthodes ou fonctionalités énumérées ci-dessous,
vous écrirez des tests unitaires qui vérifient leur bon fonctionnement.
Notez qu'une bonne pratique consiste à écrire les tests **avant** d'implémenter la fonctionalité.

Implémentez les méthodes suivantes pour le type Vecteur :

* `fn new(x: f64, y: f64) -> Vecteur` qui crée un nouveau vecteur ;
* `fn mul(self, k: f64) -> Vecteur` qui multiplie un vecteur par un flottant ;
* `fn norm(&self) -> f64` qui retourne la norme (longueur) du vecteur.

Faites ensuite en sorte que ce type implémente les traits suivants

* [`std::debut::Debug`](https://doc.rust-lang.org/std/debug/trait.Debug.html)
* [`std::clone::Clone`](https://doc.rust-lang.org/std/clone/trait.Clone.html)
* [`std::marker::Copy`](https://doc.rust-lang.org/std/marker/trait.Copy.html)
* [`std::cmp::PartialEq`](https://doc.rust-lang.org/std/cmp/trait.PartialEq.html)
* [`std::ops::Add`](https://doc.rust-lang.org/std/ops/trait.Add.html)
* [`std::ops::Sub`](https://doc.rust-lang.org/std/ops/trait.Sub.html)

## Pour aller plus loin

Le trait [`std::ops::Mul`](https://doc.rust-lang.org/std/ops/trait.Mul.html)
permet d'implémenter la multiplication entre opérateurs de type différent.

Vous pouvez donc remplacer la méthode `mul` proposée plus haut par une implementation de ce trait.