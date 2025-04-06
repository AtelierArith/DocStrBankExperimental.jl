```
rem(x, y)
%(x, y)
```

Euclidean bölme kalanı, `x` ile aynı işareti taşıyan ve `y`'den daha küçük bir değer döndürür. Bu değer her zaman tamdır.

Ayrıca bakınız: [`div`](@ref), [`mod`](@ref), [`mod1`](@ref), [`divrem`](@ref).

# Örnekler

```jldoctest
julia> x = 15; y = 4;

julia> x % y
3

julia> x == div(x, y) * y + rem(x, y)
true

julia> rem.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -2  -1  0  -2  -1  0  1  2  0  1  2
```
