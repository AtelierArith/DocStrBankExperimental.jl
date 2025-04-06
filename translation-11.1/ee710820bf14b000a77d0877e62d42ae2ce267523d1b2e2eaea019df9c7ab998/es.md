```
Tridiagonal(dl::V, d::V, du::V) donde V <: AbstractVector
```

Construye una matriz tridiagonal a partir de la primera subdiagonal, diagonal y primera superdiagonal, respectivamente. El resultado es de tipo `Tridiagonal` y proporciona solucionadores lineales especializados eficientes, pero puede convertirse en una matriz regular con [`convert(Array, _)`](@ref) (o `Array(_)` para abreviar). Las longitudes de `dl` y `du` deben ser una menos que la longitud de `d`.

!!! nota
    La subdiagonal `dl` y la superdiagonal `du` no deben estar aliasadas entre sí. Si se detecta aliasing, el constructor utilizará una copia de `du` como su argumento.


# Ejemplos

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
