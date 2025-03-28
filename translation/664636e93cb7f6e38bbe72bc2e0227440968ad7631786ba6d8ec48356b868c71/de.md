```
transpose(A)
```

Fauler Transponieren. Das Mutieren des zurückgegebenen Objekts sollte `A` entsprechend mutieren. Oft, aber nicht immer, ergibt sich `Transpose(A)`, wobei `Transpose` ein Wrapper für das faule Transponieren ist. Beachten Sie, dass diese Operation rekursiv ist.

Diese Operation ist für die Verwendung in der linearen Algebra gedacht - für allgemeine Datenmanipulation siehe [`permutedims`](@ref Base.permutedims), die nicht rekursiv ist.

# Beispiele

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # das Transponieren eines Transponierten entpackt den Elternteil
true

julia> Transpose(B) # jedoch umschließt der Konstruktor immer sein Argument
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # das Modifizieren von B wird A automatisch ändern

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

Für komplexe Matrizen ist die `adjoint`-Operation äquivalent zu einer konjugierten Transponierung.

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

Das `transpose` eines `AbstractVector` ist ein Zeilenvektor:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # gibt einen Zeilenvektor zurück
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # berechnet das Skalarprodukt
14
```

Für eine Matrix von Matrizen werden die einzelnen Blöcke rekursiv bearbeitet:

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # konstruiert eine Blockmatrix
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # Blöcke werden rekursiv transponiert
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
