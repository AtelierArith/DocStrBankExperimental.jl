```
isnumeric(c::AbstractChar) -> Bool
```

Bir karakterin sayısal olup olmadığını test eder. Bir karakter, Unicode genel kategorisi Sayı'ya ait olduğunda sayısal olarak sınıflandırılır, yani kategori kodu 'N' ile başlayan bir karakterdir.

Bu geniş kategori, ¾ ve ௰ gibi karakterleri içerir. Bir karakterin 0 ile 9 arasında bir ondalık rakam olup olmadığını kontrol etmek için [`isdigit`](@ref) kullanın.

# Örnekler

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
