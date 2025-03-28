```
permutedims(v::AbstractVector)
```

Reorganiza el vector `v` en una matriz fila de `1 × length(v)`. Se diferencia de [`transpose`](@ref) en que la operación no es recursiva, lo cual es especialmente útil para arreglos de valores no numéricos (donde la `transpose` recursiva podría lanzar un error).

# Ejemplos

A diferencia de `transpose`, `permutedims` se puede usar en vectores de elementos no numéricos arbitrarios, como cadenas:

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

Para vectores de números, `permutedims(v)` funciona de manera similar a `transpose(v)`, excepto que el tipo de retorno difiere (utiliza [`reshape`](@ref) en lugar de una vista `LinearAlgebra.Transpose`, aunque ambos comparten memoria con el arreglo original `v`):

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # mutar p o r también cambia v

julia> v # comparte memoria con ambos p y r
4-element Vector{Int64}:
 5
 6
 3
 4
```

Sin embargo, `permutedims` produce resultados que difieren de `transpose` para vectores cuyos elementos son matrices numéricas:

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
