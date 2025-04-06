```
isreal(x) -> Bool
```

Teste si `x` ou tous ses éléments sont numériquement égaux à un nombre réel, y compris les infinis et les NaNs. `isreal(x)` est vrai si `isequal(x, real(x))` est vrai.

# Exemples

```jldoctest
julia> isreal(5.)
true

julia> isreal(1 - 3im)
false

julia> isreal(Inf + 0im)
true

julia> isreal([4.; complex(0,1)])
false
```
