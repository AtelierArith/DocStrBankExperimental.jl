```
floor([T,] x)
floor(x; digits::Integer= [, base = 10])
floor(x; sigdigits::Integer= [, base = 10])
```

`floor(x)` devuelve el valor integral más cercano del mismo tipo que `x` que es menor o igual a `x`.

`floor(T, x)` convierte el resultado al tipo `T`, lanzando un `InexactError` si el valor redondeado no es representable como `T`.

Las palabras clave `digits`, `sigdigits` y `base` funcionan como para [`round`](@ref).

Para soportar `floor` para un nuevo tipo, define `Base.round(x::NewType, ::RoundingMode{:Down})`.
