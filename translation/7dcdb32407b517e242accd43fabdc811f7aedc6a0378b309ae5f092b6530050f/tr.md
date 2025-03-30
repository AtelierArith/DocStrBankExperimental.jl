```
escape_string(str::AbstractString[, esc]; keep = ())::AbstractString
escape_string(io, str::AbstractString[, esc]; keep = ())::Nothing
```

Geleneksel C ve Unicode kaçış dizilerinin genel kaçışı. İlk form kaçış dizisini döndürür, ikinci form sonucu `io`ya yazdırır.

Ters eğik çizgiler (`\`) çift ters eğik çizgi ile (`"\\"`) kaçırılır. Yazdırılamayan karakterler ya standart C kaçış kodlarıyla, NUL için `"\0"` (eğer belirsiz değilse), unicode kod noktası (`"\u"` ön eki) veya onaltılık (`"\x"` ön eki) ile kaçırılır.

İsteğe bağlı `esc` argümanı, ayrıca ters eğik çizgi ile kaçırılması gereken herhangi bir ek karakteri belirtir (`"` de ilk formda varsayılan olarak kaçırılır).

`keep` argümanı, olduğu gibi tutulması gereken karakterlerin bir koleksiyonunu belirtir. Burada `esc` önceliklidir.

Ayrıca [`unescape_string`](@ref) ters işlem için bakınız.

!!! compat "Julia 1.7"
    `keep` argümanı Julia 1.7 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> escape_string("aaa\nbbb")
"aaa\\nbbb"

julia> escape_string("aaa\nbbb"; keep = '\n')
"aaa\nbbb"

julia> escape_string("\xfe\xff") # geçersiz utf-8
"\\xfe\\xff"

julia> escape_string(string('\u2135','\0')) # belirsiz değil
"ℵ\\0"

julia> escape_string(string('\u2135','\0','0')) # \0 belirsiz olurdu
"ℵ\\x000"
```
