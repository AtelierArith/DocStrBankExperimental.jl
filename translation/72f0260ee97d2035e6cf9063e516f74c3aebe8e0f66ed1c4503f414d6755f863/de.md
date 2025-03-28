```
vcat(A...)
```

Verkettet Arrays oder Zahlen vertikal. Entspricht zu [`cat`](@ref)`(A...; dims=1)`, und zur Syntax `[a; b; c]`.

Um einen großen Vektor von Arrays zu verketten, ruft `reduce(vcat, A)` eine effiziente Methode auf, wenn `A isa AbstractVector{<:AbstractVecOrMat}` ist, anstatt paarweise zu arbeiten.

Siehe auch [`hcat`](@ref), [`Iterators.flatten`](@ref), [`stack`](@ref).

# Beispiele

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # akzeptiert Zahlen
true

julia> v == [1; 2; [3,4]]  # Syntax für die gleiche Operation
true

julia> summary(ComplexF64[1; 2; [3,4]])  # Syntax zur Angabe des Elementtyps
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # sammelt faule Bereiche
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # Zeilenvektor und eine Matrix
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # effizienter als vcat(vs...)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> ans == collect(Iterators.flatten(vs))
true
```
