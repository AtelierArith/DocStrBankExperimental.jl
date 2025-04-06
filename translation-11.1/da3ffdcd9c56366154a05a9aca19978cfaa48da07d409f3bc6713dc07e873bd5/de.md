```
mean(f, A::AbstractArray; dims)
```

Wenden Sie die Funktion `f` auf jedes Element des Arrays `A` an und berechnen Sie den Mittelwert über die Dimensionen `dims`.

!!! compat "Julia 1.3"
    Diese Methode erfordert mindestens Julia 1.3.


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
