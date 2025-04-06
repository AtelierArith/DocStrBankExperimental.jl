```
ceil([T,] x)
ceil(x; digits::Integer= [, base = 10])
ceil(x; sigdigits::Integer= [, base = 10])
```

`ceil(x)` x'in kendisinden büyük veya eşit olan en yakın tam sayı değerini döndürür.

`ceil(T, x)` sonucu `T` türüne dönüştürür, eğer yuvarlanmış değer `T` olarak temsil edilemiyorsa bir `InexactError` fırlatır.

`digits`, `sigdigits` ve `base` anahtar kelimeleri [`round`](@ref) için olduğu gibi çalışır.

Yeni bir tür için `ceil` desteği sağlamak için `Base.round(x::NewType, ::RoundingMode{:Up})` tanımlayın.
