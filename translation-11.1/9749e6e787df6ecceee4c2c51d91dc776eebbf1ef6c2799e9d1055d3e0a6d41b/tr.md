```
cld(x, y)
```

`x / y`'ye eşit veya ondan büyük en küçük tam sayı. `div(x, y, RoundUp)` ile eşdeğerdir.

Ayrıca bkz. [`div`](@ref), [`fld`](@ref).

# Örnekler

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```
