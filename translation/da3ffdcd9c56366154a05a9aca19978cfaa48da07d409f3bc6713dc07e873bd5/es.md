```
mean(f, A::AbstractArray; dims)
```

Aplica la función `f` a cada elemento del array `A` y toma la media sobre las dimensiones `dims`.

!!! compat "Julia 1.3"
    Este método requiere al menos Julia 1.3.


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
