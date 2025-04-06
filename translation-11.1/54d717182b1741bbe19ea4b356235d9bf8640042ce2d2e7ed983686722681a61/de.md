```
hcat(A...)
```

Verkettet Arrays oder Zahlen horizontal. Entspricht [`cat`](@ref)`(A...; dims=2)`, und zur Syntax `[a b c]` oder `[a;; b;; c]`.

Für einen großen Vektor von Arrays ruft `reduce(hcat, A)` eine effiziente Methode auf, wenn `A isa AbstractVector{<:AbstractVecOrMat}`. Für einen Vektor von Vektoren kann dies auch als [`stack`](@ref)`(A)` geschrieben werden.

Siehe auch [`vcat`](@ref), [`hvcat`](@ref).

# Beispiele

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # akzeptiert Zahlen
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # Syntax für die gleiche Operation
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # Syntax zur Angabe des eltype
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # effizienter als hcat(ms...)
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # stimmt nicht überein bei einem Vektor von Matrizen
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # leere Vektoren, jeweils der Größe (0,)
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # hcat mit leerer 2×0 Matrix
2×1 Matrix{Any}:
 1.1
 9.9
```
