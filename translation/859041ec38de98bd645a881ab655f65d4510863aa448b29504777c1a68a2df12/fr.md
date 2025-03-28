```
DivideError()
```

Une division entière a été tentée avec une valeur de dénominateur de 0.

# Exemples

```jldoctest
julia> 2/0
Inf

julia> div(2, 0)
ERREUR: DivideError: erreur de division entière
Trace de la pile :
[...]
```
