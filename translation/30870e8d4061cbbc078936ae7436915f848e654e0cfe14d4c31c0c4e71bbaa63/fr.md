```
|>(x, f)
```

Opérateur infixe qui applique la fonction `f` à l'argument `x`. Cela permet d'écrire `f(g(x))` sous la forme `x |> g |> f`. Lorsqu'il est utilisé avec des fonctions anonymes, des parenthèses sont généralement nécessaires autour de la définition pour obtenir la chaîne souhaitée.

# Exemples

```jldoctest
julia> 4 |> inv
0.25

julia> [2, 3, 5] |> sum |> inv
0.1

julia> [0 1; 2 3] .|> (x -> x^2) |> sum
14
```
