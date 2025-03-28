```
AssertionError([msg])
```

Die behauptete Bedingung wurde nicht als `true` ausgewertet. Das optionale Argument `msg` ist eine beschreibende Fehlermeldung.

# Beispiele

```jldoctest
julia> @assert false "this is not true"
ERROR: AssertionError: this is not true
```

`AssertionError` wird normalerweise von [`@assert`](@ref) ausgelöst.
