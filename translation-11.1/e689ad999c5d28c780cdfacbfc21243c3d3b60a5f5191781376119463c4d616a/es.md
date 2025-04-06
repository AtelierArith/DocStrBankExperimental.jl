```
latex([io::IO], md)
```

Salida el contenido del objeto Markdown `md` en formato LaTeX, ya sea escribiendo en un flujo `io` (opcional) o devolviendo una cadena.

También se puede usar `show(io, "text/latex", md)` o `repr("text/latex", md)` como alternativa.

# Ejemplos

```jldoctest
julia> latex(md"hello _world_")
"hello \\emph{world}\n\n"
```
