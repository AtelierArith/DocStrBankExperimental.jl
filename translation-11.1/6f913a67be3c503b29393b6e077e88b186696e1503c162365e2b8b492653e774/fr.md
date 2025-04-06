```
size(A::AbstractArray, [dim])
```

Renvoie un tuple contenant les dimensions de `A`. En option, vous pouvez spécifier une dimension pour obtenir uniquement la longueur de cette dimension.

Notez que `size` peut ne pas être défini pour les tableaux avec des indices non standards, auquel cas [`axes`](@ref) peut être utile. Voir le chapitre du manuel sur [les tableaux avec des indices personnalisés](@ref man-custom-indices).

Voir aussi : [`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref).

# Exemples

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
