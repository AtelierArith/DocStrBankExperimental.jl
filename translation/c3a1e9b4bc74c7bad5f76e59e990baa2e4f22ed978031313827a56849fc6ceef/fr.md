```
copy!(dst, src) -> dst
```

Copie en place [`copy`](@ref) de `src` dans `dst`, en supprimant tout élément préexistant dans `dst`. Si `dst` et `src` sont du même type, `dst == src` doit être vrai après l'appel. Si `dst` et `src` sont des tableaux multidimensionnels, ils doivent avoir des [`axes`](@ref) égaux.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


Voir aussi [`copyto!`](@ref).

!!! compat "Julia 1.1"
    Cette méthode nécessite au moins Julia 1.1. Dans Julia 1.0, cette méthode est disponible dans la bibliothèque standard `Future` sous le nom `Future.copy!`.

