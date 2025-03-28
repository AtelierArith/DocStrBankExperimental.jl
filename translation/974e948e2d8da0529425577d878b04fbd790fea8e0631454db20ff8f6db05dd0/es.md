```
gcd(x, y...)
```

Máximo común divisor (positivo) (o cero si todos los argumentos son cero). Los argumentos pueden ser números enteros y racionales.

!!! compat "Julia 1.4"
    Los argumentos racionales requieren Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> gcd(6, 9)
3

julia> gcd(6, -9)
3

julia> gcd(6, 0)
6

julia> gcd(0, 0)
0

julia> gcd(1//3, 2//3)
1//3

julia> gcd(1//3, -2//3)
1//3

julia> gcd(1//3, 2)
1//3

julia> gcd(0, 0, 10, 15)
5
```
