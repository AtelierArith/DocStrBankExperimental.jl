```
cumprod!(y::AbstractVector, x::AbstractVector)
```

Bir vektör `x`'in kümülatif çarpımını alır ve sonucu `y`'ye kaydeder. Ayrıca bkz. [`cumprod`](@ref).

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
