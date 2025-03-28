```
stack(iter; [dims])
```

Combinez une collection de tableaux (ou d'autres objets itérables) de taille égale en un tableau plus grand, en les arrangeant le long d'une ou plusieurs nouvelles dimensions.

Par défaut, les axes des éléments sont placés en premier, donnant `size(result) = (size(first(iter))..., size(iter)...)`. Cela a le même ordre d'éléments que [`Iterators.flatten`](@ref)`(iter)`.

Avec le mot-clé `dims::Integer`, au lieu de cela, le `i`-ème élément de `iter` devient la tranche [`selectdim`](@ref)`(result, dims, i)`, de sorte que `size(result, dims) == length(iter)`. Dans ce cas, `stack` inverse l'action de [`eachslice`](@ref) avec les mêmes `dims`.

Les diverses fonctions [`cat`](@ref) combinent également des tableaux. Cependant, celles-ci étendent toutes les dimensions existantes (possiblement triviales) des tableaux, plutôt que de placer les tableaux le long de nouvelles dimensions. Elles acceptent également des tableaux en tant qu'arguments séparés, plutôt qu'une seule collection.

!!! compat "Julia 1.9"
    Cette fonction nécessite au moins Julia 1.9.


# Exemples

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

julia> stack(zip(1:4, 10:99))  # accepte n'importe quel itérateur d'itérateurs
2×4 Matrix{Int64}:
  1   2   3   4
 10  11  12  13

julia> vec(ans) == collect(Iterators.flatten(zip(1:4, 10:99)))
true

julia> stack(vecs; dims=1)  # contrairement à toute fonction cat, le 1er axe de vecs[1] est le 2ème axe du résultat
3×2 Matrix{Float32}:
   1.0    2.0
  30.0   40.0
 500.0  600.0

julia> x = rand(3,4);

julia> x == stack(eachcol(x)) == stack(eachrow(x), dims=1)  # inverse de eachslice
true
```

Exemples de dimensions supérieures :

```jldoctest
julia> A = rand(5, 7, 11);

julia> E = eachslice(A, dims=2);  # un vecteur de matrices

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

julia> stack(M) |> size  # garde toutes les dimensions
(2, 3, 5, 7)

julia> stack(M; dims=1) |> size  # vec(container) le long de dims=1
(35, 2, 3)

julia> hvcat(5, M...) |> size  # hvcat met les matrices côte à côte
(14, 15)
```
