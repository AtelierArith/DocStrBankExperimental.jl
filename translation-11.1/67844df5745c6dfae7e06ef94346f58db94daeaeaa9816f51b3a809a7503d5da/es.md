```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

Imprime los códigos de bits LLVM generados para ejecutar el método que coincide con la función genérica y la firma de tipo dadas en `io`.

Si la palabra clave `optimize` no está establecida, el código se mostrará antes de las optimizaciones de LLVM. Todos los metadatos y las llamadas a dbg.* se eliminan del código de bits impreso. Para el IR completo, establece la palabra clave `raw` en true. Para volcar todo el módulo que encapsula la función (con declaraciones), establece la palabra clave `dump_module` en true. El argumento de palabra clave `debuginfo` puede ser uno de source (predeterminado) o none, para especificar la verbosidad de los comentarios del código.

Ver también: [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref).
