```
displaysize([io::IO]) -> (lines, columns)
```

Devuelve el tamaño nominal de la pantalla que puede ser utilizada para renderizar la salida a este objeto `IO`. Si no se proporciona ninguna entrada, se leen las variables de entorno `LINES` y `COLUMNS`. Si no están configuradas, se devuelve un tamaño predeterminado de `(24, 80)`.

# Ejemplos

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

Para obtener el tamaño de tu TTY,

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
