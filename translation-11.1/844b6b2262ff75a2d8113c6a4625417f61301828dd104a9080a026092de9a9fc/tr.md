```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

Bir hexadecimal dizesini temsil eden byte'ların `itr` adlı iterable'ını ikili temsiline dönüştürür; [`hex2bytes`](@ref) ile benzerlik gösterir, ancak çıktı `dest`'e yerinde yazılır. `dest`'in uzunluğu `itr`'nin uzunluğunun yarısı olmalıdır.

!!! compat "Julia 1.7"
    UInt8 üreten iteratörlerle hex2bytes! çağrısı 1.7 sürümünü gerektirir. Daha önceki sürümlerde, çağrımdan önce iterable'ı toplamanız gerekir.

