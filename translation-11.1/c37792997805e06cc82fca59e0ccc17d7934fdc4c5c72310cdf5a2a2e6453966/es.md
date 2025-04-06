```
html([io::IO], md)
```

Salida el contenido del objeto Markdown `md` en formato HTML, ya sea escribiendo en un flujo `io` (opcional) o devolviendo una cadena.

Se puede usar alternativamente `show(io, "text/html", md)` o `repr("text/html", md)`, que difieren en que envuelven la salida en un elemento `<div class="markdown"> ... </div>`.

# Ejemplos

```jldoctest
julia> html(md"hello _world_")
"<p>hello <em>world</em></p>\n"
```
