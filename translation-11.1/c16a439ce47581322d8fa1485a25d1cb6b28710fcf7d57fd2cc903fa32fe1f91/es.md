```
display(x)
display(d::AbstractDisplay, x)
display(mime, x)
display(d::AbstractDisplay, mime, x)
```

Muestra `x` utilizando la visualización más aplicable en la pila de visualización, típicamente usando la salida multimedia más rica soportada para `x`, con salida de texto plano [`stdout`](@ref) como respaldo. La variante `display(d, x)` intenta mostrar `x` solo en la visualización dada `d`, lanzando un [`MethodError`](@ref) si `d` no puede mostrar objetos de este tipo.

En general, no puedes asumir que la salida de `display` va a `stdout` (a diferencia de [`print(x)`](@ref) o [`show(x)`](@ref)). Por ejemplo, `display(x)` puede abrir una ventana separada con una imagen. `display(x)` significa "muestra `x` de la mejor manera que puedas para el(los) dispositivo(s) de salida actuales." Si deseas una salida de texto similar a REPL que esté garantizada para ir a `stdout`, usa [`show(stdout, "text/plain", x)`](@ref) en su lugar.

También hay dos variantes con un argumento `mime` (una cadena de tipo MIME, como `"image/png"`), que intentan mostrar `x` utilizando el tipo MIME solicitado *solo*, lanzando un `MethodError` si este tipo no es soportado ni por la(s) visualización(es) ni por `x`. Con estas variantes, también se puede proporcionar los datos "crudos" en el tipo MIME solicitado pasando `x::AbstractString` (para tipos MIME con almacenamiento basado en texto, como text/html o application/postscript) o `x::Vector{UInt8}` (para tipos MIME binarios).

Para personalizar cómo se muestran las instancias de un tipo, sobrecarga [`show`](@ref) en lugar de `display`, como se explica en la sección del manual sobre [impresión bonita personalizada](@ref man-custom-pretty-printing).
