```
isunaryoperator(s::Symbol)
```

Gibt `true` zurück, wenn das Symbol als unärer (Präfix-)Operator verwendet werden kann, andernfalls `false`.

# Beispiele

```jldoctest
julia> Meta.isunaryoperator(:-), Meta.isunaryoperator(:√), Meta.isunaryoperator(:f)
(true, true, false)
```
