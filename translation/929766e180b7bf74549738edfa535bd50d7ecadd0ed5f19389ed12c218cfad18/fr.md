```
copyto!(dest::AbstractArray, src) -> dest
```

Copie tous les éléments de la collection `src` vers le tableau `dest`, dont la longueur doit être supérieure ou égale à la longueur `n` de `src`. Les premiers `n` éléments de `dest` sont écrasés, les autres éléments restent inchangés.

Voir aussi [`copy!`](@ref Base.copy!), [`copy`](@ref).

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
