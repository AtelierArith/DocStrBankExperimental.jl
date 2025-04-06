```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

`str`'den baştaki ve sondaki karakterleri kaldırır; bu ya `chars` ile belirtilen karakterler ya da `pred` fonksiyonunun `true` döndürdüğü karakterlerdir.

Varsayılan davranış, baştaki ve sondaki boşluk ve ayırıcıları kaldırmaktır: kesin ayrıntılar için [`isspace`](@ref) bölümüne bakın.

İsteğe bağlı `chars` argümanı, kaldırılacak karakterleri belirtir: bu tek bir karakter, karakter vektörü veya karakter kümesi olabilir.

Ayrıca [`lstrip`](@ref) ve [`rstrip`](@ref) bölümlerine de bakın.

!!! compat "Julia 1.2"
    Bir predikat fonksiyonu kabul eden yöntem, Julia 1.2 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
