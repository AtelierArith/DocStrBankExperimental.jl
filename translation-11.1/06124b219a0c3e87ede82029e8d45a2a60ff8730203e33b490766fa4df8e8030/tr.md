```
transcode(T, src)
```

Unicode kodlamaları arasında dize verilerini dönüştürür. `src`, ya bir `String` ya da UTF-XX kod birimlerinin `Vector{UIntXX}`'sidir; burada `XX` 8, 16 veya 32'dir. `T`, dönüş değerinin kodlamasını belirtir: (UTF-8 kodlu) bir `String` döndürmek için `String` veya UTF-`XX` verilerinin bir `Vector{UIntXX}`'sini döndürmek için `UIntXX`. (Dış C kütüphaneleri tarafından kullanılan `wchar_t*` dizelerini dönüştürmek için tam sayı türü olarak [`Cwchar_t`](@ref) de kullanılabilir.)

`transcode` fonksiyonu, giriş verileri hedef kodlamada makul bir şekilde temsil edilebildiği sürece başarılı olur; geçersiz Unicode verileri için bile, UTF-XX kodlamaları arasında dönüşümler için her zaman başarılıdır.

Şu anda yalnızca UTF-8'e/UTF-8'den dönüşüm desteklenmektedir.

# Örnekler

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
