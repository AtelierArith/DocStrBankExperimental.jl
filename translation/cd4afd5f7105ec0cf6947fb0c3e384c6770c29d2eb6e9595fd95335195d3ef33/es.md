```
struct SimpleColor
```

Una representación básica de un color, destinada a propósitos de estilo de cadena. Puede contener un color nombrado (como `:red`), o un `RGBTuple` que es un NamedTuple que especifica un color `r`, `g`, `b` con una profundidad de bits de 8.

# Constructores

```julia
SimpleColor(name::Symbol)  # p. ej. :red
SimpleColor(rgb::RGBTuple) # p. ej. (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # p. ej. 0x123456
```

También consulta `tryparse(SimpleColor, rgb::String)`.
