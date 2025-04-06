```
typeassert(x, type)
```

Lève une [`TypeError`](@ref) à moins que `x isa type`. La syntaxe `x::type` appelle cette fonction.

# Exemples

```jldoctest
julia> typeassert(2.5, Int)
ERROR: TypeError: in typeassert, expected Int64, got a value of type Float64
Stacktrace:
[...]
```
