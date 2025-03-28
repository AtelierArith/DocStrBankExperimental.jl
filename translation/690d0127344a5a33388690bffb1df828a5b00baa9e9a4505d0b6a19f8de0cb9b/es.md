```
isreal(x) -> Bool
```

Prueba si `x` o todos sus elementos son numéricamente iguales a algún número real, incluyendo infinitos y NaNs. `isreal(x)` es verdadero si `isequal(x, real(x))` es verdadero.

# Ejemplos

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
