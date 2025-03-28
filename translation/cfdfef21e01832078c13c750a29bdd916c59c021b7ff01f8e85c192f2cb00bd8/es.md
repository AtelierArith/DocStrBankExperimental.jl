```
ceil([T,] x)
ceil(x; digits::Integer= [, base = 10])
ceil(x; sigdigits::Integer= [, base = 10])
```

`ceil(x)` devuelve el valor integral más cercano del mismo tipo que `x` que es mayor o igual a `x`.

`ceil(T, x)` convierte el resultado al tipo `T`, lanzando un `InexactError` si el valor redondeado no es representable como un `T`.

Las palabras clave `digits`, `sigdigits` y `base` funcionan como para [`round`](@ref).

Para soportar `ceil` para un nuevo tipo, define `Base.round(x::NewType, ::RoundingMode{:Up})`.
