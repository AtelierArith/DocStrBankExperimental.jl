```
reverse(A; dims=:)
```

`A`'yı `dims` boyutu boyunca ters çevirir; bu, bir tam sayı (tek bir boyut), bir tam sayı demeti (bir boyut demeti) veya `:` (tüm boyutlar boyunca ters çevir, varsayılan) olabilir. Yerinde ters çevirme için ayrıca [`reverse!`](@ref) bakın.

# Örnekler

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    Julia 1.6'dan önce, `reverse`'da yalnızca tek tam sayı `dims` desteklenmektedir.

