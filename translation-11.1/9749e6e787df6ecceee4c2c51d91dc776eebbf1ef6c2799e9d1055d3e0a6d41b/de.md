```
cld(x, y)
```

Kleinste ganze Zahl, die größer oder gleich `x / y` ist. Entspricht `div(x, y, RoundUp)`.

Siehe auch [`div`](@ref), [`fld`](@ref).

# Beispiele

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) mit eltype Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```
