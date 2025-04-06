```
code_warntype([io::IO], f, types; debuginfo=:default)
```

Imprime ASTs bajados e inferidos por tipo para los métodos que coinciden con la función genérica dada y la firma de tipo a `io`, que por defecto es `stdout`. Los ASTs están anotados de tal manera que los tipos "no hoja" que pueden ser problemáticos para el rendimiento se enfatizan (si hay color disponible, se muestran en rojo). Esto sirve como una advertencia de posible inestabilidad de tipo.

No todos los tipos no hoja son particularmente problemáticos para el rendimiento, y las características de rendimiento de un tipo particular son un detalle de implementación del compilador. `code_warntype` errará del lado de colorear los tipos de rojo si podrían ser una preocupación de rendimiento, por lo que algunos tipos pueden estar coloreados de rojo incluso si no impactan el rendimiento. Pequeñas uniones de tipos concretos generalmente no son una preocupación, por lo que se destacan en amarillo.

El argumento clave `debuginfo` puede ser uno de `:source` o `:none` (por defecto), para especificar la verbosidad de los comentarios de código.

Consulta la sección [`@code_warntype`](@ref man-code-warntype) en la página de Consejos de Rendimiento del manual para más información.

Consulta también: [`@code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref), [`code_native`](@ref).
