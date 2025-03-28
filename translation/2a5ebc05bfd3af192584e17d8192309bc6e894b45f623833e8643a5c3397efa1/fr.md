```
mod(x, y)
rem(x, y, RoundDown)
```

La réduction de `x` modulo `y`, ou équivalemment, le reste de `x` après division entière par `y`, c'est-à-dire `x - y*fld(x,y)` si calculé sans arrondi intermédiaire.

Le résultat aura le même signe que `y`, et une magnitude inférieure à `abs(y)` (avec quelques exceptions, voir la note ci-dessous).

!!! note
    Lorsqu'il est utilisé avec des valeurs à virgule flottante, le résultat exact peut ne pas être représentable par le type, et donc une erreur d'arrondi peut se produire. En particulier, si le résultat exact est très proche de `y`, il peut être arrondi à `y`.


Voir aussi : [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
