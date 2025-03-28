```
typeassert(x, type)
```

Wirft einen [`TypeError`](@ref), es sei denn, `x isa type`. Die Syntax `x::type` ruft diese Funktion auf.

# Beispiele

```jldoctest
julia> typeassert(2.5, Int)
ERROR: TypeError: in typeassert, expected Int64, got a value of type Float64
Stacktrace:
[...]
```
