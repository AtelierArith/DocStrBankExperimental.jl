```
randperm([rng=default_rng(),] n::Integer)
```

Construye una permutación aleatoria de longitud `n`. El argumento opcional `rng` especifica un generador de números aleatorios (ver [Números Aleatorios](@ref)). El tipo de elemento del resultado es el mismo que el tipo de `n`.

Para permutar aleatoriamente un vector arbitrario, consulta [`shuffle`](@ref) o [`shuffle!`](@ref).

!!! compat "Julia 1.1"
    En Julia 1.1 `randperm` devuelve un vector `v` con `eltype(v) == typeof(n)` mientras que en Julia 1.0 `eltype(v) == Int`.


# Ejemplos

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
