```
stack(iter; [dims])
```

Kombiniert eine Sammlung von Arrays (oder anderen iterierbaren Objekten) gleicher Größe zu einem größeren Array, indem sie entlang einer oder mehrerer neuer Dimensionen angeordnet werden.

Standardmäßig werden die Achsen der Elemente zuerst platziert, was `size(result) = (size(first(iter))..., size(iter)...)` ergibt. Dies hat die gleiche Reihenfolge der Elemente wie [`Iterators.flatten`](@ref)`(iter)`.

Mit dem Schlüsselwort `dims::Integer` wird stattdessen das `i`-te Element von `iter` zur Scheibe [`selectdim`](@ref)`(result, dims, i)`, sodass `size(result, dims) == length(iter)` gilt. In diesem Fall kehrt `stack` die Aktion von [`eachslice`](@ref) mit denselben `dims` um.

Die verschiedenen [`cat`](@ref) Funktionen kombinieren ebenfalls Arrays. Diese erweitern jedoch alle die bestehenden (möglicherweise trivialen) Dimensionen der Arrays, anstatt die Arrays entlang neuer Dimensionen zu platzieren. Sie akzeptieren auch Arrays als separate Argumente, anstatt als eine einzige Sammlung.

!!! compat "Julia 1.9"
    Diese Funktion erfordert mindestens Julia 1.9.


# Beispiele

```jldoctest
julia> vecs = (1:2, [30, 40], Float32[500, 600]);

julia> mat = stack(vecs)
2×3 Matrix{Float32}:
 1.0  30.0  500.0
 2.0  40.0  600.0

julia> mat == hcat(vecs...) == reduce(hcat, collect(vecs))
true

julia> vec(mat) == vcat(vecs...) == reduce(vcat, collect(vecs))
true

julia> stack(zip(1:4, 10:99))  # akzeptiert beliebige Iteratoren von Iteratoren
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # im Gegensatz zu jeder cat-Funktion ist die 1. Achse von vecs[1] die 2. Achse des Ergebnisses
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # Umkehrung von eachslice
true
```

Höherdimensionale Beispiele:

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # ein Vektor von Matrizen

julia> (element = size(first(E)), container = size(E))
(element = (5, 11), container = (7,))

julia> stack(E) |> size
(5, 11, 7)

julia> stack(E) == stack(E; dims=3) == cat(E...; dims=3)
true

julia> A == stack(E; dims=2)
true

julia> M = (fill(10i+j, 2, 3) for i in 1:5, j in 1:7);

julia> (element = size(first(M)), container = size(M))
(element = (2, 3), container = (5, 7))

julia> stack(M) |> size  # behält alle Dimensionen
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # vec(container) entlang dims=1
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat platziert Matrizen nebeneinander
(14, 15)
```
