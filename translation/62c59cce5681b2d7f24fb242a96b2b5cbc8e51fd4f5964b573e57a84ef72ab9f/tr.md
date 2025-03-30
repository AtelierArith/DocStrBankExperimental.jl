```
ispunct(c::AbstractChar) -> Bool
```

Bir karakterin Unicode genel kategorisi Noktalama işaretine ait olup olmadığını test eder, yani kategori kodu 'P' ile başlayan bir karakterdir.

# Örnekler

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
