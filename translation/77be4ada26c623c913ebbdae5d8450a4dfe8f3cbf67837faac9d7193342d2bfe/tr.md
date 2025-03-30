```
exp(x)
```

`x`'in doğal taban üstelini hesaplayın, diğer bir deyişle $ℯ^x$.

Ayrıca bkz. [`exp2`](@ref), [`exp10`](@ref) ve [`cis`](@ref).

# Örnekler

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
