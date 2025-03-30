```
ccall((function_name, library), returntype, (argtype1, ...), argvalue1, ...)
ccall(function_name, returntype, (argtype1, ...), argvalue1, ...)
ccall(function_pointer, returntype, (argtype1, ...), argvalue1, ...)
```

C'den dışa aktarılan bir paylaşımlı kütüphanedeki bir işlevi çağırın; bu, `(function_name, library)` demetinde belirtilmiştir; her bir bileşen ya bir dize ya da bir semboldür. Bir kütüphane belirtmek yerine, mevcut süreçte çözümlenen bir `function_name` sembolü veya dizesi de kullanılabilir. Alternatif olarak, `ccall`, `dlsym` ile döndürülen bir işlev işaretçisi `function_pointer` çağırmak için de kullanılabilir.

Argüman türü demetinin bir literal demet olması gerektiğini ve bir demet-değerli değişken veya ifade olmaması gerektiğini unutmayın.

`ccall`'a verilen her `argvalue`, otomatik olarak `unsafe_convert(argtype, cconvert(argtype, argvalue))` çağrıları eklenerek karşılık gelen `argtype`'a dönüştürülecektir. (Daha fazla ayrıntı için [`unsafe_convert`](@ref Base.unsafe_convert) ve [`cconvert`](@ref Base.cconvert) belgelerine de bakın.) Çoğu durumda, bu basitçe `convert(argtype, argvalue)` çağrısına yol açar.
