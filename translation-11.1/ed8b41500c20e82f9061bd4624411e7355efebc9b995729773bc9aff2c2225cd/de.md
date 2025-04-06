```
front(x::Tuple)::Tuple
```

Gibt ein `Tuple` zurück, das aus allen Komponenten von `x` besteht, außer der letzten.

Siehe auch: [`first`](@ref), [`tail`](@ref Base.tail).

# Beispiele

```jldoctest
julia> Base.front((1,2,3))
(1, 2)

julia> Base.front(())
ERROR: ArgumentError: Kann front nicht auf einem leeren Tuple aufrufen.
```
