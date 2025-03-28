```
isone(x)
```

Gibt `true` zurück, wenn `x == one(x)`; wenn `x` ein Array ist, überprüft dies, ob `x` eine Identitätsmatrix ist.

# Beispiele

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
