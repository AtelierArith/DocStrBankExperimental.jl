```
mean(A::AbstractArray; dims)
```

Verilen boyutlar üzerinde bir dizinin ortalamasını hesaplayın.

!!! compat "Julia 1.1"
    Boş diziler için `mean` en az Julia 1.1 gerektirir.


# Örnekler

```jldoctest
julia> using Statistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> mean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
