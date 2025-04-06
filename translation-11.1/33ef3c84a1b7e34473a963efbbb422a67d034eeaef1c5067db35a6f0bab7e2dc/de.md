```
cat(A...; dims)
```

Verkettet die Eingabearrays entlang der in `dims` angegebenen Dimensionen.

Entlang einer Dimension `d in dims` ist die Größe des Ausgabearrays `sum(size(a,d) for a in A)`. In anderen Dimensionen sollten alle Eingabearrays die gleiche Größe haben, die auch die Größe des Ausgabearrays in diesen Dimensionen sein wird.

Wenn `dims` eine einzelne Zahl ist, werden die verschiedenen Arrays entlang dieser Dimension eng gepackt. Wenn `dims` eine iterable Struktur ist, die mehrere Dimensionen enthält, werden die Positionen entlang dieser Dimensionen gleichzeitig für jedes Eingabearray erhöht, wobei an anderen Stellen mit Null aufgefüllt wird. Dies ermöglicht es, block-diagonale Matrizen zu konstruieren, wie `cat(matrices...; dims=(1,2))`, und deren höherdimensionale Analogien.

Der Sonderfall `dims=1` ist [`vcat`](@ref), und `dims=2` ist [`hcat`](@ref). Siehe auch [`hvcat`](@ref), [`hvncat`](@ref), [`stack`](@ref), [`repeat`](@ref).

Das Schlüsselwort akzeptiert auch `Val(dims)`.

!!! compat "Julia 1.8"
    Für mehrere Dimensionen wurde `dims = Val(::Tuple)` in Julia 1.8 hinzugefügt.


# Beispiele

Verkette zwei Arrays in verschiedenen Dimensionen:

```jldoctest
julia> a = [1 2 3]
1×3 Matrix{Int64}:
 1  2  3

julia> b = [4 5 6]
1×3 Matrix{Int64}:
 4  5  6

julia> cat(a, b; dims=1)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> cat(a, b; dims=2)
1×6 Matrix{Int64}:
 1  2  3  4  5  6

julia> cat(a, b; dims=(1, 2))
2×6 Matrix{Int64}:
 1  2  3  0  0  0
 0  0  0  4  5  6
```

# Erweiterte Hilfe

Verkette 3D-Arrays:

```jldoctest
julia> a = ones(2, 2, 3);

julia> b = ones(2, 2, 4);

julia> c = cat(a, b; dims=3);

julia> size(c) == (2, 2, 7)
true
```

Verkette Arrays unterschiedlicher Größen:

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # dasselbe wie hcat
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0
```

Konstruiere eine block-diagonale Matrix:

```
julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # block-diagonal
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1
```

```
julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```

!!! note
    `cat` verbindet keine zwei Strings, du möchtest vielleicht `*` verwenden.


```jldoctest
julia> a = "aaa";

julia> b = "bbb";

julia> cat(a, b; dims=1)
2-element Vector{String}:
 "aaa"
 "bbb"

julia> cat(a, b; dims=2)
1×2 Matrix{String}:
 "aaa"  "bbb"

julia> a * b
"aaabbb"
```
