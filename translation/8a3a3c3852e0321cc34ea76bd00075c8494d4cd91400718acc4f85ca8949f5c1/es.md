```
@code_native
```

Evalúa los argumentos de la llamada a la función o macro, determina sus tipos y llama a [`code_native`](@ref) en la expresión resultante.

Establece cualquiera de los argumentos opcionales `syntax`, `debuginfo`, `binary` o `dump_module` colocándolo antes de la llamada a la función, así:

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * Establece la sintaxis de ensamblador configurando `syntax` a `:intel` (predeterminado) para la sintaxis Intel o `:att` para la sintaxis AT&T.
  * Especifica la verbosidad de los comentarios de código configurando `debuginfo` a `:source` (predeterminado) o `:none`.
  * Si `binary` es `true`, también imprime el código de máquina binario para cada instrucción precedido por una dirección abreviada.
  * Si `dump_module` es `false`, no imprime metadatos como rodata o directivas.

Consulta también: [`code_native`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref).
