```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

Bir karakterin ASCII karakter setine ait olup olmadığını veya bir dizi içindeki tüm elemanlar için bunun doğru olup olmadığını test eder.

# Örnekler

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

Örneğin, `isascii` fonksiyonu [`filter`](@ref) veya [`replace`](@ref) için bir predikat fonksiyonu olarak kullanılabilir; sırasıyla ASCII olmayan karakterleri kaldırmak veya değiştirmek için:

```jldoctest
julia> filter(isascii, "abcdeγfgh") # ASCII olmayan karakterleri at
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # ASCII olmayan karakterleri boşluklarla değiştir
"abcde fgh"
```
