```
tryparse(::Type{SimpleColor}, rgb::String)
```

`rgb`'yi bir `SimpleColor` olarak ayrıştırmayı deneyin. Eğer `rgb` `#` ile başlıyorsa ve uzunluğu 7 ise, `RGBTuple` destekli bir `SimpleColor`'a dönüştürülür. Eğer `rgb` `a`-`z` ile başlıyorsa, `rgb` bir renk adı olarak yorumlanır ve `Symbol` destekli bir `SimpleColor`'a dönüştürülür.

Aksi takdirde, `nothing` döndürülür.

# Örnekler

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```
