```
isletter(c::AbstractChar) -> Bool
```

Bir karakterin harf olup olmadığını test eder. Bir karakter, Unicode genel kategorisi Harf'e ait olduğunda, yani kategori kodu 'L' ile başlayan bir karakter olduğunda harf olarak sınıflandırılır.

Ayrıca bkz: [`isdigit`](@ref).

# Örnekler

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
