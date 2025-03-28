```
front(x::Tuple)::Tuple
```

Retourne un `Tuple` consistant de tous les composants sauf le dernier de `x`.

Voir aussi : [`first`](@ref), [`tail`](@ref Base.tail).

# Exemples

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
ERROR: ArgumentError: Cannot call front on an empty tuple.
```
