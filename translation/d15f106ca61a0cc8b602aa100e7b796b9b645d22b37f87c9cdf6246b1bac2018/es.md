```
dot(x, A, y)
```

Calcula el producto punto generalizado `dot(x, A*y)` entre dos vectores `x` y `y`, sin almacenar el resultado intermedio de `A*y`. Al igual que para el [`dot(_,_)`](@ref) de dos argumentos, esto actúa de manera recursiva. Además, para vectores complejos, el primer vector se conjuga.

!!! compat "Julia 1.4"
    `dot` de tres argumentos requiere al menos Julia 1.4.


# Ejemplos

```jldoctest
julia> dot([1; 1], [1 2; 3 4], [2; 3])
26

julia> dot(1:5, reshape(1:25, 5, 5), 2:6)
4850

julia> ⋅(1:5, reshape(1:25, 5, 5), 2:6) == dot(1:5, reshape(1:25, 5, 5), 2:6)
true
```
