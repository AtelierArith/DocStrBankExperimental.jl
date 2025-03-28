```
accumulate!(op, B, A; [dims], [init])
```

Opération cumulative `op` sur `A` le long de la dimension `dims`, stockant le résultat dans `B`. Fournir `dims` est optionnel pour les vecteurs. Si l'argument clé `init` est donné, sa valeur est utilisée pour instancier l'accumulation.

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


Voir aussi [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref).

# Exemples

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
