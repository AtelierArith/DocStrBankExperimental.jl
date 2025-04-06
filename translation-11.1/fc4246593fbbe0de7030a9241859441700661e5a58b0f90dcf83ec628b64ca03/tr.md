```
lpad(s, n::Integer, p::Union{AbstractChar,AbstractString}=' ') -> String
```

`s`'yi string'e çevirir ve elde edilen string'i `p` ile soldan doldurarak `n` karakter ([`textwidth`](@ref)) uzunluğunda hale getirir. Eğer `s` zaten `n` karakter uzunluğundaysa, eşit bir string döndürülür. Varsayılan olarak boşluklarla doldurur.

# Örnekler

```jldoctest
julia> lpad("March", 10)
"     March"
```

!!! compat "Julia 1.7"
    Julia 1.7'de, bu fonksiyon ham karakter (kod noktası) sayısı yerine `textwidth` kullanacak şekilde değiştirildi.

