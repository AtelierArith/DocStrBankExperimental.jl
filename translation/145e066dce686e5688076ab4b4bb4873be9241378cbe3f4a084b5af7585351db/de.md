```
isoperator(s::Symbol)
```

Gibt `true` zurück, wenn das Symbol als Operator verwendet werden kann, andernfalls `false`.

# Beispiele

```jldoctest
julia> Meta.isoperator(:+), Meta.isoperator(:f)
(true, false)
```
