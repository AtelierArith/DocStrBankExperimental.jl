```
tail(x::Tuple)::Tuple
```

Renvoie un `Tuple` contenant tous les composants sauf le premier de `x`.

Voir aussi : [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# Exemples

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
ERROR: ArgumentError: Cannot call tail on an empty tuple.
```
