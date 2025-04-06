```
isvalid(T, value) -> Bool
```

Verilen değerin o tür için geçerli olup olmadığını kontrol eder. Türler şu anda ya `AbstractChar` ya da `String` olabilir. `AbstractChar` için değerler `AbstractChar` türünde veya [`UInt32`](@ref) türünde olabilir. `String` için değerler o türde, `SubString{String}`, `Vector{UInt8}` veya bunların bitişik bir alt dizisi olabilir.

# Örnekler

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    Alt dizi değerleri için destek Julia 1.6'da eklendi.

