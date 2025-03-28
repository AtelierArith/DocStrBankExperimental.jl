```
lcm(x, y...)
```

Múltiplo común (positivo) mínimo (o cero si algún argumento es cero). Los argumentos pueden ser números enteros y racionales.

!!! compat "Julia 1.4"
    Los argumentos racionales requieren Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> lcm(2, 3)
6

julia> lcm(-2, 3)
6

julia> lcm(0, 3)
0

julia> lcm(0, 0)
0

julia> lcm(1//3, 2//3)
2//3

julia> lcm(1//3, -2//3)
2//3

julia> lcm(1//3, 2)
2//1

julia> lcm(1, 3, 5, 7)
105
```
