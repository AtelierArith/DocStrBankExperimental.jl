```
struct SimpleColor
```

Une représentation de base d'une couleur, destinée à des fins de stylisation de chaîne. Elle peut contenir soit une couleur nommée (comme `:red`), soit un `RGBTuple` qui est un NamedTuple spécifiant une couleur `r`, `g`, `b` avec une profondeur de bits de 8.

# Constructeurs

```julia
SimpleColor(name::Symbol)  # par ex. :red
SimpleColor(rgb::RGBTuple) # par ex. (r=1, b=2, g=3)
SimpleColor(r::Integer, b::Integer, b::Integer)
SimpleColor(rgb::UInt32)   # par ex. 0x123456
```

Voir aussi `tryparse(SimpleColor, rgb::String)`.
