```
Float32(x [, mode::RoundingMode])
```

`x`'den bir `Float32` oluşturur. Eğer `x` tam olarak temsil edilemiyorsa, `mode` `x`'in nasıl yuvarlandığını belirler.

# Örnekler

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

Mevcut yuvarlama modları için [`RoundingMode`](@ref) kısmına bakın. ```
