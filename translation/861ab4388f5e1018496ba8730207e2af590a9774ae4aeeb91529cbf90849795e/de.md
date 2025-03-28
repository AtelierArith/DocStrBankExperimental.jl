```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

Permutieren Sie die Dimensionen (Achsen) des Arrays `A`. `perm` ist ein Tupel oder Vektor von `ndims(A)` Ganzzahlen, die die Permutation angeben.

Wenn `A` ein 2D-Array ([`AbstractMatrix`](@ref)) ist, dann ist `perm` standardmäßig `(2,1)`, was die beiden Achsen von `A` (die Zeilen und Spalten der Matrix) vertauscht. Dies unterscheidet sich von [`transpose`](@ref), da die Operation nicht rekursiv ist, was besonders nützlich für Arrays mit nicht-numerischen Werten ist (wo die rekursive `transpose` einen Fehler auslösen würde) und/oder 2D-Arrays, die keine linearen Operatoren darstellen.

Für 1D-Arrays siehe [`permutedims(v::AbstractVector)`](@ref), das eine 1-Zeilen-“Matrix” zurückgibt.

Siehe auch [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref).

# Beispiele

## 2D-Arrays:

Im Gegensatz zu `transpose` kann `permutedims` verwendet werden, um Zeilen und Spalten von 2D-Arrays beliebiger nicht-numerischer Elemente, wie z.B. Strings, zu vertauschen:

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

Und `permutedims` liefert Ergebnisse, die sich von `transpose` für Matrizen unterscheiden, deren Elemente selbst numerische Matrizen sind:

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

## Mehrdimensionale Arrays

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # die letzte Dimension zuerst setzen

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # die inverse Permutation
true
```

Für jede Dimension `i` von `B = permutedims(A, perm)` wird die entsprechende Dimension von `A` `perm[i]` sein. Das bedeutet, dass die Gleichheit `size(B, i) == size(A, perm[i])` gilt.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
