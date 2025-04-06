```
tryparse(::Type{SimpleColor}, rgb::String)
```

Versuchen Sie, `rgb` als `SimpleColor` zu parsen. Wenn `rgb` mit `#` beginnt und eine Länge von 7 hat, wird es in einen `RGBTuple`-unterstützten `SimpleColor` umgewandelt. Wenn `rgb` mit `a`-`z` beginnt, wird `rgb` als Farbname interpretiert und in einen `Symbol`-unterstützten `SimpleColor` umgewandelt.

Andernfalls wird `nothing` zurückgegeben.

# Beispiele

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```
