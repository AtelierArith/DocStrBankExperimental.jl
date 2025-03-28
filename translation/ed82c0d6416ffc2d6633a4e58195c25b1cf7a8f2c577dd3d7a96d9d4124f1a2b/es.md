```
flipsign(x, y)
```

Devuelve `x` con su signo cambiado si `y` es negativo. Por ejemplo `abs(x) = flipsign(x,x)`.

# Ejemplos

```jldoctest
julia> flipsign(5, 3)
5

julia> flipsign(5, -3)
-5
```
