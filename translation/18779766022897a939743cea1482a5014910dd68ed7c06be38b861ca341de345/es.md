```
parse(str; raise=true, depwarn=true, filename="none")
```

Analiza la cadena de expresión de manera codiciosa, devolviendo una única expresión. Se lanza un error si hay caracteres adicionales después de la primera expresión. Si `raise` es `true` (por defecto), los errores de sintaxis generarán un error; de lo contrario, `parse` devolverá una expresión que generará un error al evaluarse. Si `depwarn` es `false`, se suprimirán las advertencias de deprecación. El argumento `filename` se utiliza para mostrar diagnósticos cuando se lanza un error.

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
ERROR: ParseError:
# Error @ none:1:1
1.0.2
└──┘ ── constante numérica inválida
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "constante numérica inválida "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "incompleto: fin prematuro de la entrada")))
```
