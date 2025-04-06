```
isbinaryoperator(s::Symbol)
```

Gibt `true` zurück, wenn das Symbol als binärer (Infix-)Operator verwendet werden kann, andernfalls `false`.

# Beispiele

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
