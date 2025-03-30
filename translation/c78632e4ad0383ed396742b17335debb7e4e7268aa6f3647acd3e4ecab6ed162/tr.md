```
read(io::IO, T)
```

`io`'dan `T` türünde tek bir değeri, kanonik ikili temsilinde okuyun.

Julia'nın sonlandırma düzenini sizin için dönüştürmediğini unutmayın. Bu amaçla [`ntoh`](@ref) veya [`ltoh`](@ref) kullanın.

```
read(io::IO, String)
```

`io`'nun tamamını bir `String` olarak okuyun (bkz. ayrıca [`readchomp`](@ref)).

# Örnekler

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, Char)
'J': ASCII/Unicode U+004A (kategori Lu: Harf, büyük)

julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> read(io, String)
"JuliaLang is a GitHub organization"
```
