```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

Permuta las dimensiones (ejes) del arreglo `A`. `perm` es una tupla o vector de `ndims(A)` enteros que especifican la permutación.

Si `A` es un arreglo 2d ([`AbstractMatrix`](@ref)), entonces `perm` por defecto es `(2,1)`, intercambiando los dos ejes de `A` (las filas y columnas de la matriz). Esto difiere de [`transpose`](@ref) en que la operación no es recursiva, lo cual es especialmente útil para arreglos de valores no numéricos (donde la `transpose` recursiva lanzaría un error) y/o arreglos 2d que no representan operadores lineales.

Para arreglos 1d, consulta [`permutedims(v::AbstractVector)`](@ref), que devuelve una “matriz” de 1 fila.

Consulta también [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref).

# Ejemplos

## Arreglos 2d:

A diferencia de `transpose`, `permutedims` se puede usar para intercambiar filas y columnas de arreglos 2d de elementos no numéricos arbitrarios, como cadenas:

```jldoctest
julia> A = ["a" "b" "c"
            "d" "e" "f"]
2×3 Matrix{String}:
 "a"  "b"  "c"
 "d"  "e"  "f"

julia> permutedims(A)
3×2 Matrix{String}:
 "a"  "d"
 "b"  "e"
 "c"  "f"
```

Y `permutedims` produce resultados que difieren de `transpose` para matrices cuyos elementos son a su vez matrices numéricas:

```jldoctest; setup = :(using LinearAlgebra)
julia> a = [1 2; 3 4];

julia> b = [5 6; 7 8];

julia> c = [9 10; 11 12];

julia> d = [13 14; 15 16];

julia> X = [[a] [b]; [c] [d]]
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]     [5 6; 7 8]
 [9 10; 11 12]  [13 14; 15 16]

julia> permutedims(X)
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [9 10; 11 12]
 [5 6; 7 8]  [13 14; 15 16]

julia> transpose(X)
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [9 11; 10 12]
 [5 7; 6 8]  [13 15; 14 16]
```

## Arreglos multidimensionales

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # poner la última dimensión primero

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # la permutación inversa
true
```

Para cada dimensión `i` de `B = permutedims(A, perm)`, su dimensión correspondiente de `A` será `perm[i]`. Esto significa que la igualdad `size(B, i) == size(A, perm[i])` se cumple.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
