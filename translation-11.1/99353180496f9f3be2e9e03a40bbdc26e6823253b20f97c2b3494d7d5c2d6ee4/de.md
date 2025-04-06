```
tail(x::Tuple)::Tuple
```

Gibt ein `Tuple` zurück, das aus allen Komponenten von `x` besteht, außer der ersten.

Siehe auch: [`front`](@ref Base.front), [`rest`](@ref Base.rest), [`first`](@ref), [`Iterators.peel`](@ref).

# Beispiele

```jldoctest
julia> Base.tail((1,2,3))
(2, 3)

julia> Base.tail(())
ERROR: ArgumentError: Kann tail nicht auf einem leeren Tuple aufrufen.
```
