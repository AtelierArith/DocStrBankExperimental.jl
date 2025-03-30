```
Float64(x [, mode::RoundingMode])
```

`x`'den bir `Float64` oluşturur. Eğer `x` tam olarak temsil edilemiyorsa, `mode` `x`'in nasıl yuvarlanacağını belirler.

# Örnekler

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

Mevcut yuvarlama modları için [`RoundingMode`](@ref) kısmına bakın. ```
