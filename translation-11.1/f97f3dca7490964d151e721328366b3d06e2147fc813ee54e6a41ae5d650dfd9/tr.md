```
floor([T,] x)
floor(x; digits::Integer= [, base = 10])
floor(x; sigdigits::Integer= [, base = 10])
```

`floor(x)` ifadesi, `x`'e eşit veya daha küçük olan `x` ile aynı türdeki en yakın tam sayıyı döndürür.

`floor(T, x)` sonucu `T` türüne dönüştürür, eğer yuvarlanmış değer `T` olarak temsil edilemiyorsa bir `InexactError` fırlatır.

`digits`, `sigdigits` ve `base` anahtar kelimeleri [`round`](@ref) için olduğu gibi çalışır.

Yeni bir tür için `floor` desteği sağlamak için, `Base.round(x::NewType, ::RoundingMode{:Down})` tanımlayın.
