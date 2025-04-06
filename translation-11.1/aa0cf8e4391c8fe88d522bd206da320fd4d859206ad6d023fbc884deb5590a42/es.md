```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

Analiza la cadena de expresión y devuelve una expresión (que podría ser pasada a eval para su ejecución). `start` es el índice de unidad de código en `str` del primer carácter desde el cual comenzar a analizar (como con todos los índices de cadena, estos no son índices de caracteres). Si `greedy` es `true` (por defecto), `parse` intentará consumir la mayor cantidad de entrada posible; de lo contrario, se detendrá tan pronto como haya analizado una expresión válida. Las expresiones incompletas pero de otro modo sintácticamente válidas devolverán `Expr(:incomplete, "(mensaje de error)")`. Si `raise` es `true` (por defecto), los errores de sintaxis que no sean expresiones incompletas generarán un error. Si `raise` es `false`, `parse` devolverá una expresión que generará un error al ser evaluada. Si `depwarn` es `false`, se suprimirán las advertencias de deprecación. El argumento `filename` se utiliza para mostrar diagnósticos cuando se genera un error.

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # inicio de la cadena
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # final de la cadena
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # índice de 3
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
