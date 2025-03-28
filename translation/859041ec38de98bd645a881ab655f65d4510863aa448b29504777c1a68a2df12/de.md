```
DivideError()
```

Es wurde eine ganzzahlige Division mit einem Nennerwert von 0 versucht.

# Beispiele

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
ERROR: DivideError: ganzzahlige Division Fehler
Stacktrace:
[...]
```
