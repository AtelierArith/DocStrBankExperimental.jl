```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

`str`'den sonundaki karakterleri kaldırır, ya `chars` ile belirtilenler ya da `pred` fonksiyonunun `true` döndürdüğü karakterler.

Varsayılan davranış, sonundaki boşlukları ve ayırıcıları kaldırmaktır: kesin detaylar için [`isspace`](@ref) bölümüne bakın.

İsteğe bağlı `chars` argümanı, kaldırılacak karakterleri belirtir: bu tek bir karakter veya bir karakter vektörü veya kümesi olabilir.

Ayrıca [`strip`](@ref) ve [`lstrip`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> a = rpad("Mart", 20)
"Mart               "

julia> rstrip(a)
"Mart"
```
