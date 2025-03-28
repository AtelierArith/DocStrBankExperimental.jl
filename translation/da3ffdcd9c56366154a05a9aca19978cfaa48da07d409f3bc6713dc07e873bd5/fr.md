```
mean(f, A::AbstractArray; dims)
```

Applique la fonction `f` à chaque élément du tableau `A` et prend la moyenne sur les dimensions `dims`.

!!! compat "Julia 1.3"
    Cette méthode nécessite au moins Julia 1.3.


```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908

julia> mean(√, [1 2 3; 4 5 6], dims=2)
2×1 Matrix{Float64}:
 1.3820881233139908
 2.2285192400943226
```
