```
@code_llvm
```

Evalúa los argumentos de la función o llamada a macro, determina sus tipos y llama a [`code_llvm`](@ref) en la expresión resultante. Establece los argumentos opcionales `raw`, `dump_module`, `debuginfo`, `optimize` colocando estos y su valor antes de la llamada a la función, así:

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize` controla si se aplican optimizaciones adicionales, como la inlining. `raw` hace que todos los metadatos y llamadas dbg.* sean visibles. `debuginfo` puede ser uno de `:source` (por defecto) o `:none`, para especificar la verbosidad de los comentarios del código. `dump_module` imprime todo el módulo que encapsula la función.

Ver también: [`code_llvm`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_native`](@ref).
