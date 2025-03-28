```
tryparse(::Type{SimpleColor}, rgb::String)
```

Intenta analizar `rgb` como un `SimpleColor`. Si `rgb` comienza con `#` y tiene una longitud de 7, se convierte en un `SimpleColor` respaldado por un `RGBTuple`. Si `rgb` comienza con `a`-`z`, `rgb` se interpreta como un nombre de color y se convierte en un `SimpleColor` respaldado por un `Symbol`.

De lo contrario, se devuelve `nothing`.

# Ejemplos

```jldoctest; setup = :(import StyledStrings.SimpleColor)
julia> tryparse(SimpleColor, "blue")
SimpleColor(blue)

julia> tryparse(SimpleColor, "#9558b2")
SimpleColor(#9558b2)

julia> tryparse(SimpleColor, "#nocolor")
```
