```
copysign(x, y) -> z
```

Devuelve `z` que tiene la magnitud de `x` y el mismo signo que `y`.

# Ejemplos

```jldoctest
julia> copysign(1, -2)
-1

julia> copysign(-1, 2)
1
```
