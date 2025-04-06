```
escape_raw_string(s::AbstractString, delim='"') -> AbstractString
escape_raw_string(io, s::AbstractString, delim='"')
```

Ham bir dizeyi ham dize literalleri için ayrıştırma sırasında kullanılan şekilde kaçış yapar. Girdi dizesindeki her çift tırnak (`"`) karakteri için `s` (veya belirtilmişse `delim`), bu fonksiyon önceki ters eğik çizgi (`\`) karakterlerinin sayısını *n* olarak sayar ve ardından *n*'den 2*n*+1'e kadar ters eğik çizgilerin sayısını artırır (n = 0 için bile). Ayrıca, dize sonundaki ters eğik çizgi dizisini de iki katına çıkarır.

Bu kaçış kuralı, ham dizelerde ve diğer standart dışı dize literallerinde kullanılır. (Ayrıca, Microsoft C/C++ derleyici çalışma zamanının bir komut satırı dizesini argv[] dizisine ayrıştırırken beklediği kaçış kuralıdır.)

Ayrıca [`escape_string`](@ref) bakınız.
