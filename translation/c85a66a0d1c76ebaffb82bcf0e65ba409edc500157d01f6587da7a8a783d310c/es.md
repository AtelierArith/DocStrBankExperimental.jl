```
showable(mime, x)
```

Devuelve un valor booleano que indica si el objeto `x` se puede escribir como el tipo `mime` dado.

(Por defecto, esto se determina automáticamente por la existencia del método correspondiente [`show`](@ref) para `typeof(x)`. Algunos tipos proporcionan métodos `showable` personalizados; por ejemplo, si los formatos MIME disponibles dependen del *valor* de `x`.)

# Ejemplos

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```
