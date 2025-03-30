```
CFunction yapısı
```

`@cfunction` ile dönen değerin çöp toplama işlemi için '$' ile işaretlenmiş ilk argüman kullanıldığında. Tüm `cfunction` tutucuları gibi, `ccall`'e `Ptr{Cvoid}` olarak geçirilmelidir ve çağrı noktasında otomatik olarak uygun türe dönüştürülecektir.

[`@cfunction`](@ref) bakınız.
