```
randcycle([rng=default_rng(),] n::Integer)
```

Construye una permutación cíclica aleatoria de longitud `n`. El argumento opcional `rng` especifica un generador de números aleatorios, consulta [Random Numbers](@ref). El tipo de elemento del resultado es el mismo que el tipo de `n`.

Aquí, una "permutación cíclica" significa que todos los elementos están dentro de un solo ciclo. Si `n > 0`, hay $(n-1)!$ posibles permutaciones cíclicas, que se muestrean uniformemente. Si `n == 0`, `randcycle` devuelve un vector vacío.

[`randcycle!`](@ref) es una variante en su lugar de esta función.

!!! compat "Julia 1.1"
    En Julia 1.1 y versiones posteriores, `randcycle` devuelve un vector `v` con `eltype(v) == typeof(n)` mientras que en Julia 1.0 `eltype(v) == Int`.


# Ejemplos

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
