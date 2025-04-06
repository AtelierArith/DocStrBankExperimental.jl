```
vcat(A...)
```

Concaténer des tableaux ou des nombres verticalement. Équivalent à [`cat`](@ref)`(A...; dims=1)`, et à la syntaxe `[a; b; c]`.

Pour concaténer un grand vecteur de tableaux, `reduce(vcat, A)` appelle une méthode efficace lorsque `A isa AbstractVector{<:AbstractVecOrMat}`, plutôt que de travailler par paires.

Voir aussi [`hcat`](@ref), [`Iterators.flatten`](@ref), [`stack`](@ref).

# Exemples

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # accepte les nombres
true

julia> v == [1; 2; [3,4]]  # syntaxe pour la même opération
true

julia> summary(ComplexF64[1; 2; [3,4]])  # syntaxe pour fournir le type d'élément
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # collecte des plages paresseuses
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # vecteur ligne et une matrice
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # plus efficace que vcat(vs...)
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
