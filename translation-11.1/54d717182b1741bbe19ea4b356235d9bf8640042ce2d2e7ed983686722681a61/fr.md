```
hcat(A...)
```

Concaténer des tableaux ou des nombres horizontalement. Équivalent à [`cat`](@ref)`(A...; dims=2)`, et à la syntaxe `[a b c]` ou `[a;; b;; c]`.

Pour un grand vecteur de tableaux, `reduce(hcat, A)` appelle une méthode efficace lorsque `A isa AbstractVector{<:AbstractVecOrMat}`. Pour un vecteur de vecteurs, cela peut également être écrit [`stack`](@ref)`(A)`.

Voir aussi [`vcat`](@ref), [`hvcat`](@ref).

# Exemples

```jldoctest
julia> hcat([1,2], [3,4], [5,6])
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> hcat(1, 2, [30 40], [5, 6, 7]')  # accepte les nombres
1×7 Matrix{Int64}:
 1  2  30  40  5  6  7

julia> ans == [1 2 [30 40] [5, 6, 7]']  # syntaxe pour la même opération
true

julia> Float32[1 2 [30 40] [5, 6, 7]']  # syntaxe pour fournir le type d'élément
1×7 Matrix{Float32}:
 1.0  2.0  30.0  40.0  5.0  6.0  7.0

julia> ms = [zeros(2,2), [1 2; 3 4], [50 60; 70 80]];

julia> reduce(hcat, ms)  # plus efficace que hcat(ms...)
2×6 Matrix{Float64}:
 0.0  0.0  1.0  2.0  50.0  60.0
 0.0  0.0  3.0  4.0  70.0  80.0

julia> stack(ms) |> summary  # désaccord sur un vecteur de matrices
"2×2×3 Array{Float64, 3}"

julia> hcat(Int[], Int[], Int[])  # vecteurs vides, chacun de taille (0,)
0×3 Matrix{Int64}

julia> hcat([1.1, 9.9], Matrix(undef, 2, 0))  # hcat avec une matrice 2×0 vide
2×1 Matrix{Any}:
 1.1
 9.9
```
