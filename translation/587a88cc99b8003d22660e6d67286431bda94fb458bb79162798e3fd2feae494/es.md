```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

Imprime las instrucciones de ensamblaje nativo generadas para ejecutar el método que coincide con la función genérica y la firma de tipo dadas en `io`.

  * Establece la sintaxis de ensamblaje configurando `syntax` a `:intel` (predeterminado) para la sintaxis intel o `:att` para la sintaxis AT&T.
  * Especifica la verbosidad de los comentarios de código configurando `debuginfo` a `:source` (predeterminado) o `:none`.
  * Si `binary` es `true`, también imprime el código de máquina binario para cada instrucción precedido por una dirección abreviada.
  * Si `dump_module` es `false`, no imprime metadatos como rodata o directivas.
  * Si `raw` es `false`, se omiten instrucciones poco interesantes (como el prólogo de la función de safepoint).

Ver también: [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref).
