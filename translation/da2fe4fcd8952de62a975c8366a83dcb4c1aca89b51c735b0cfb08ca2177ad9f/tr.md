```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

`s`'den `suffix`'i kaldırır. Eğer `s`, `suffix` ile bitmiyorsa, `s`'ye eşit bir dize döndürülür.

Ayrıca [`chopprefix`](@ref) bakınız.

!!! compat "Julia 1.8"
    Bu fonksiyon Julia 1.8 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
