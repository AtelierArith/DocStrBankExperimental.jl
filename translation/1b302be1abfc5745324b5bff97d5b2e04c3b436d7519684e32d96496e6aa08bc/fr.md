```
tryparse(::Type{SimpleColor}, rgb::String)
```

Tente de parser `rgb` en tant que `SimpleColor`. Si `rgb` commence par `#` et a une longueur de 7, il est converti en un `SimpleColor` soutenu par un `RGBTuple`. Si `rgb` commence par `a`-`z`, `rgb` est interprété comme un nom de couleur et converti en un `SimpleColor` soutenu par un `Symbol`.

Sinon, `nothing` est retourné.

# Exemples

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```
