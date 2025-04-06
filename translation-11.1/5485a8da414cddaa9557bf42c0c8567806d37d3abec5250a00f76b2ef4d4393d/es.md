```
repr(mime, x; context=nothing)
```

Devuelve un `AbstractString` o `Vector{UInt8}` que contiene la representación de `x` en el tipo `mime` solicitado, tal como lo escribe [`show(io, mime, x)`](@ref) (lanzando un [`MethodError`](@ref) si no hay un `show` apropiado disponible). Se devuelve un `AbstractString` para tipos MIME con representaciones textuales (como `"text/html"` o `"application/postscript"`), mientras que los datos binarios se devuelven como `Vector{UInt8}`. (La función `istextmime(mime)` devuelve si Julia trata un tipo `mime` dado como texto.)

El argumento de palabra clave opcional `context` se puede establecer como un par `:key=>value` o un objeto `IO` o [`IOContext`](@ref) cuyas atributos se utilizan para el flujo de I/O pasado a `show`.

Como caso especial, si `x` es un `AbstractString` (para tipos MIME textuales) o un `Vector{UInt8}` (para tipos MIME binarios), la función `repr` asume que `x` ya está en el formato `mime` solicitado y simplemente devuelve `x`. Este caso especial no se aplica al tipo MIME `"text/plain"`. Esto es útil para que los datos en bruto se puedan pasar a `display(m::MIME, x)`.

En particular, `repr("text/plain", x)` es típicamente una versión "bien formateada" de `x` diseñada para el consumo humano.  Véase también [`repr(x)`](@ref) para devolver en su lugar una cadena correspondiente a [`show(x)`](@ref) que puede estar más cerca de cómo se ingresaría el valor de `x` en Julia.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4];

julia> repr("text/plain", A)
"2×2 Matrix{Int64}:\n 1  2\n 3  4"
```
