```
median(A::AbstractArray; dims)
```

Verilen boyutlar boyunca bir dizinin medyanını hesaplar.

# Örnekler

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
