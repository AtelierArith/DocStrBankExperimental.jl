```
Base.checked_length(r)
```

`length(r)`'yi hesaplar, ancak sonuç `Union{Integer(eltype(r)),Int}` içine sığmadığında, uygun olduğunda taşma hatalarını kontrol edebilir.
