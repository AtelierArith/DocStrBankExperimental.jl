```
@MIME_str
```

Una macro de conveniencia para escribir tipos de [`MIME`](@ref), típicamente utilizada al agregar métodos a [`show`](@ref). Por ejemplo, la sintaxis `show(io::IO, ::MIME"text/html", x::MyType) = ...` podría usarse para definir cómo escribir una representación HTML de `MyType`.
