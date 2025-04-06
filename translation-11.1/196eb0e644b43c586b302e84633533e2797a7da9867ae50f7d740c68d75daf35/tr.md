```
isbitstype(T)
```

`T` türü "sade veri" türü ise `true` döndürür; bu, değişmez olduğu ve yalnızca `primitive` türler ve diğer `isbitstype` türleri içeren başka değerlere referans içermediği anlamına gelir. Tipik örnekler arasında [`UInt8`](@ref), [`Float64`](@ref) ve [`Complex{Float64}`](@ref) gibi sayısal türler bulunmaktadır. Bu türler, tür parametreleri olarak geçerli oldukları, [`isdefined`](@ref) / [`isassigned`](@ref) durumunu takip etmeyebilecekleri ve C ile uyumlu tanımlı bir düzenleri olduğu için önemlidir. Eğer `T` bir tür değilse, `false` döndürün.

Ayrıca bkz. [`isbits`](@ref), [`isprimitivetype`](@ref), [`ismutable`](@ref).

# Örnekler

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
