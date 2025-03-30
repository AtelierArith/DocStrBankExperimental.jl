```
asin(x)
```

`x`'in tersine sinüsünü hesaplar, çıktı radyan cinsindendir.

Ayrıca [`asind`](@ref) ile derece cinsinden çıktı için bakınız.

# Örnekler

```jldoctest
julia> asin.((0, 1/2, 1))
(0.0, 0.5235987755982989, 1.5707963267948966)

julia> asind.((0, 1/2, 1))
(0.0, 30.000000000000004, 90.0)
```
