```
unescape_string(str::AbstractString, keep = ())::AbstractString
unescape_string(io, s::AbstractString, keep = ())::Nothing
```

Geleneksel C ve Unicode kaçış dizilerinin genel çözülmesi. İlk form, kaçış dizisini döndürür, ikincisi sonucu `io`'ya yazdırır. `keep` argümanı, olduğu gibi tutulacak karakterlerin (ve ters eğik çizgilerin) bir koleksiyonunu belirtir.

Aşağıdaki kaçış dizileri tanınır:

  * Kaçış ters eğik çizgi (`\\`)
  * Kaçış çift tırnak (`\"`)
  * Standart C kaçış dizileri (`\a`, `\b`, `\t`, `\n`, `\v`, `\f`, `\r`, `\e`)
  * Unicode BMP kod noktaları (`\u` ile 1-4 ardışık onaltılık basamak)
  * Tüm Unicode kod noktaları (`\U` ile 1-8 ardışık onaltılık basamak; maksimum değer = 0010ffff)
  * Onaltılık baytlar (`\x` ile 1-2 ardışık onaltılık basamak)
  * Sekizli baytlar (`\` ile 1-3 ardışık sekizli basamak)

Ayrıca [`escape_string`](@ref) bakınız.

# Örnekler

```jldoctest
julia> unescape_string("aaa\\nbbb") # C kaçış dizisi
"aaa\nbbb"

julia> unescape_string("\\u03c0") # unicode
"π"

julia> unescape_string("\\101") # sekizli
"A"

julia> unescape_string("aaa \\g \\n", ['g']) # `keep` argümanını kullanma
"aaa \\g \n"
```
