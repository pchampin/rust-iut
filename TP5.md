# TP n°5

Créez un nouveau projet nommé `tp5` avec la ligne de commande `cargo new --lib tp5`.

Vous constaterez que le répertoire `src` ne contient pas de fichier `main.rs`,
mais un fichier `lib.rs`.
Ce projet ne sert pas à créer un fichier exécutable,
mais une bibliothèque réutilisable par d'autres.

## Tests unitaires

Vous constaterez que le fichier `lib.rs` contient les lignes suivantes :

```rust
#[cfg(test)]
mod tests {
    #[test]
    fn it_works() {
        assert_eq!(2 + 2, 4);
    }
}
```

* La directive `#[cfg(test)]` indique au compilateur que le module `tests`
  doit être compilé *uniquement* pour exécuter les tests unitaires.
* La directive `#[test]` est utilisée pour indiquer qu'une fonction est un test unitaire.
* Un test unitaire est considéré comme un succès s'il ne panique pas.
* La macro `assert_eq!(x, y)` panique si les deux valeurs passées sont différentes.
* Une autre macro `assert!(x)` panique si la valeur passée est `false`.

Ajoutez dans le module `tests` la fonction suivante :
```rust
#[test]
fn test0() {
    assert!(1+1 == 3);
}
```

Pour lancer les tests, utilisez la commande `cargo test`,
et constatez que `test0` échoue.
Modifiez le code pour faire en sorte qu'il réussisse, et lancez `cargo test` à nouveau.


## Le type `Vecteur`

Votre travail consiste maintenant à définir un type `Vecteur`
représentant un vecteur dans un espace à deux dimensions.

Pour chacune des méthodes ou fonctionnalités énumérées ci-dessous,
vous écrirez des tests unitaires qui vérifient leur bon fonctionnement.
Notez qu'une bonne pratique consiste à écrire les tests **avant** d'implémenter la fonctionnalité.

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

Vous pouvez donc remplacer la méthode `mul` proposée plus haut par une implémentation de ce trait.
