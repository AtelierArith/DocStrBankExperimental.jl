```
LinearIndices(A::AbstractArray)
```

Devuelve un array `LinearIndices` con la misma forma y [`axes`](@ref) que `A`, conteniendo el índice lineal de cada entrada en `A`. Indexar este array con índices cartesianos permite mapearlos a índices lineales.

Para arrays con indexación convencional (los índices comienzan en 1), o cualquier array multidimensional, los índices lineales varían de 1 a `length(A)`. Sin embargo, para `AbstractVector`s, los índices lineales son `axes(A, 1)`, y por lo tanto no comienzan en 1 para vectores con indexación no convencional.

Llamar a esta función es la forma "segura" de escribir algoritmos que explotan la indexación lineal.

# Ejemplos

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

Devuelve un array `LinearIndices` con la forma especificada o [`axes`](@ref).

# Ejemplos

El propósito principal de este constructor es la conversión intuitiva de la indexación cartesiana a la indexación lineal:

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
