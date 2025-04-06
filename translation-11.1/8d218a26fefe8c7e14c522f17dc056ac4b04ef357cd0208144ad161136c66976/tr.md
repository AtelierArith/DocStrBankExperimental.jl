```
isunordered(x)
```

`x` değeri [`<`](@ref) ile sıralanabilir değilse, örneğin `NaN` veya `missing` ise `true` döner.

Bu predikat ile `true` olarak değerlendirilen değerler, [`isless`](@ref) gibi diğer sıralamalarla sıralanabilir olabilir.

!!! compat "Julia 1.7"
    Bu fonksiyon Julia 1.7 veya daha yenisini gerektirir.

