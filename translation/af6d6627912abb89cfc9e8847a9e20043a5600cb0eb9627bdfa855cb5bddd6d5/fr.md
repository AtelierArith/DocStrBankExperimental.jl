```
IteratorSize(itertype::Type) -> IteratorSize
```

Étant donné le type d'un itérateur, renvoie l'une des valeurs suivantes :

  * `SizeUnknown()` si la longueur (nombre d'éléments) ne peut pas être déterminée à l'avance.
  * `HasLength()` s'il y a une longueur fixe et finie.
  * `HasShape{N}()` s'il y a une longueur connue plus une notion de forme multidimensionnelle (comme pour un tableau). Dans ce cas, `N` doit donner le nombre de dimensions, et la fonction [`axes`](@ref) est valide pour l'itérateur.
  * `IsInfinite()` si l'itérateur produit des valeurs indéfiniment.

La valeur par défaut (pour les itérateurs qui ne définissent pas cette fonction) est `HasLength()`. Cela signifie que la plupart des itérateurs sont supposés implémenter [`length`](@ref).

Ce trait est généralement utilisé pour sélectionner entre des algorithmes qui pré-allouent de l'espace pour leur résultat, et des algorithmes qui redimensionnent leur résultat de manière incrémentielle.

```jldoctest
julia> Base.IteratorSize(1:5)
Base.HasShape{1}()

julia> Base.IteratorSize((2,3))
Base.HasLength()
```
