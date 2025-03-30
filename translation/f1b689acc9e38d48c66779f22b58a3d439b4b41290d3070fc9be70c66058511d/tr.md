```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

`prefix`'i `s`'den kaldır. Eğer `s`, `prefix` ile başlamıyorsa, `s`'ye eşit bir string döndürülür.

Ayrıca bkz. [`chopsuffix`](@ref).

!!! compat "Julia 1.8"
    Bu fonksiyon Julia 1.8 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
