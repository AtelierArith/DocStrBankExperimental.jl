```
struct SimpleColor
```

Eine grundlegende Darstellung einer Farbe, die für die Formatierung von Zeichenfolgen gedacht ist. Sie kann entweder eine benannte Farbe (wie `:red`) oder ein `RGBTuple` enthalten, das ein NamedTuple ist, das eine `r`, `g`, `b` Farbe mit einer Farbtiefe von 8 angibt.

# Konstruktoren

```julia
SimpleColor(name::Symbol)  # z.B. :red
SimpleColor(rgb::RGBTuple) # z.B. (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # z.B. 0x123456
```

Siehe auch `tryparse(SimpleColor, rgb::String)`.
