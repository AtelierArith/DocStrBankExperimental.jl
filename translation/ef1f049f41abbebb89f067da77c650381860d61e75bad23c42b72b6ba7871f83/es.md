```
@raw_str -> String
```

Crea una cadena sin procesar sin interpolación ni desescapado. La excepción es que las comillas aún deben ser escapadas. Las barras invertidas escapan tanto las comillas como otras barras invertidas, pero solo cuando una secuencia de barras invertidas precede a un carácter de comillas. Así, 2n barras invertidas seguidas de una comilla codifican n barras invertidas y el final del literal, mientras que 2n+1 barras invertidas seguidas de una comilla codifican n barras invertidas seguidas de un carácter de comillas.

# Ejemplos

```jldoctest
julia> println(raw"\ $x")
\ $x

julia> println(raw"\"")
"

julia> println(raw"\\\"")
\"

julia> println(raw"\\x \\\"")
\\x \"
```
