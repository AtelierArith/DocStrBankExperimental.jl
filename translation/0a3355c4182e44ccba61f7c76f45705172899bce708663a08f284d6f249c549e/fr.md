```
zip(iters...)
```

Exécute plusieurs itérateurs en même temps, jusqu'à ce que l'un d'eux soit épuisé. Le type de valeur de l'itérateur `zip` est un tuple de valeurs de ses sous-itérateurs.

!!! note
    `zip` ordonne les appels à ses sous-itérateurs de telle sorte que les itérateurs avec état ne progresseront pas lorsque un autre itérateur se termine dans l'itération en cours.


!!! note
    `zip()` sans arguments produit un itérateur infini de tuples vides.


Voir aussi : [`enumerate`](@ref), [`Base.splat`](@ref).

# Exemples

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
