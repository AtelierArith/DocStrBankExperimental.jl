```
reinterpret(::Type{Out}, x::In)
```

İkili verinin `x` isbits değerindeki tür yorumlamasını `isbits` türü `Out` olarak değiştirir. `Out`'un boyutu (doldurma hariç) `x` türünün boyutuyla aynı olmalıdır. Örneğin, `reinterpret(Float32, UInt32(7))` `UInt32(7)` ile ilişkili 4 baytı bir [`Float32`](@ref) olarak yorumlar. `reinterpret(In, reinterpret(Out, x)) === x` olduğunu unutmayın.

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! not
    Doldurma işleminin ele alınışı `reinterpret(::DataType, ::AbstractArray)` ile farklıdır.


!!! uyarı     `Out` içindeki bazı bit kombinasyonları geçerli olarak kabul edilmediğinde ve türün yapıcıları ve yöntemleri tarafından engellenmediğinde dikkatli olun. Ek doğrulama olmadan beklenmedik davranışlar ortaya çıkabilir.
