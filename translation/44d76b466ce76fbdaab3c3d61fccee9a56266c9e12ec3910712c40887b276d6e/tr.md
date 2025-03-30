```
isvalid(s::AbstractString, i::Integer) -> Bool
```

Verilen indeksin `s` içindeki bir karakterin kodlamasının başlangıcı olup olmadığını belirten bir predikattir. Eğer `isvalid(s, i)` doğruysa, `s[i]` o indekste başlayan karakteri döndürecektir; eğer yanlışsa, `s[i]` geçersiz bir indeks hatası veya `i` sınırda ise bir sınır hatası verecektir. `isvalid(s, i)`'nin O(1) bir fonksiyon olabilmesi için, `s`'nin kodlaması [kendinden senkronize](https://en.wikipedia.org/wiki/Self-synchronizing_code) olmalıdır. Bu, Julia'nın genel dize desteği için temel bir varsayımdır.

Ayrıca [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref) bakınız.

# Örnekler

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (kategori Ll: Harf, küçük)

julia> isvalid(str, 2)
false

julia> str[2]
HATA: StringIndexError: geçersiz indeks [2], geçerli yakın indeksler [1]=>'α', [3]=>'β'
Yığın izi:
[...]
```
