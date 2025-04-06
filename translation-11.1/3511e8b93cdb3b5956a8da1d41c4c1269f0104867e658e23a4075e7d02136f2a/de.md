```
vect(X...)
```

Erstellt einen [`Vector`](@ref) mit einem Elementtyp, der aus dem `promote_typeof` des Arguments berechnet wird, und enthält die Argumentliste.

# Beispiele

```jldoctest
julia> a = Base.vect(UInt8(1), 2.5, 1//2)
3-element Vector{Float64}:
 1.0
 2.5
 0.5
```
