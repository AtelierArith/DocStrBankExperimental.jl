```
typeof(x)
```

`x`'in somut türünü al.

Ayrıca bkz. [`eltype`](@ref).

# Örnekler

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias for Array{Float64, 2})
```
