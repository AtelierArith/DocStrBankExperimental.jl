```
Regex(pattern[, flags]) <: AbstractPattern
```

Bir düzenli ifade temsil eden bir türdür. `Regex` nesneleri, dizeleri [`match`](@ref) ile eşleştirmek için kullanılabilir.

`Regex` nesneleri, [`@r_str`](@ref) dize makrosu kullanılarak oluşturulabilir. `Regex(pattern[, flags])` yapıcı genellikle `pattern` dizesinin interpolasyona ihtiyaç duyduğu durumlarda kullanılır. Bayraklar hakkında daha fazla bilgi için dize makrosunun belgelerine bakın.

!!! not
    İnterpolasyon yapılmış değişkenleri kaçırmak için `\Q` ve `\E` kullanın (örneğin, `Regex("\\Q$x\\E")`)

