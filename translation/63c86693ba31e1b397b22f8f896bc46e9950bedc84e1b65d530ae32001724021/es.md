```
typeassert(x, type)
```

Lanza un [`TypeError`](@ref) a menos que `x isa type`. La sintaxis `x::type` llama a esta función.

# Ejemplos

```jldoctest
julia> typeassert(2.5, Int)
ERROR: TypeError: in typeassert, expected Int64, got a value of type Float64
Stacktrace:
[...]
```
