```
count([f=identity,] itr; init=0) -> Integer
```

Comptez le nombre d'éléments dans `itr` pour lesquels la fonction `f` renvoie `true`. Si `f` est omis, comptez le nombre d'éléments `true` dans `itr` (qui devrait être une collection de valeurs booléennes). `init` spécifie en option la valeur à partir de laquelle commencer le comptage et détermine donc également le type de sortie.

!!! compat "Julia 1.6"
    Le mot-clé `init` a été ajouté dans Julia 1.6.


Voir aussi : [`any`](@ref), [`sum`](@ref).

# Exemples

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
