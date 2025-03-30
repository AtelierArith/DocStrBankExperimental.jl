```
lstrip([pred=isspace,] str::AbstractString) -> SubString
lstrip(str::AbstractString, chars) -> SubString
```

`str`'den önde bulunan karakterleri kaldırır, ya `chars` ile belirtilenler ya da `pred` fonksiyonunun `true` döndürdüğü karakterler.

Varsayılan davranış, önde bulunan boşluk ve ayırıcıları kaldırmaktır: kesin detaylar için [`isspace`](@ref) bölümüne bakın.

İsteğe bağlı `chars` argümanı, kaldırılacak karakterleri belirtir: bu tek bir karakter veya bir karakter vektörü ya da kümesi olabilir.

Ayrıca [`strip`](@ref) ve [`rstrip`](@ref) bölümlerine de bakın.

# Örnekler

```jldoctest
julia> a = lpad("Mart", 20)
"               Mart"

julia> lstrip(a)
"Mart"
```
