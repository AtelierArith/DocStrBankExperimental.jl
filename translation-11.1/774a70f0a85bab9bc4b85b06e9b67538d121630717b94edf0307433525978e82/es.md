```
@code_typed
```

Evalúa los argumentos de la llamada a la función o macro, determina sus tipos y llama a [`code_typed`](@ref) en la expresión resultante. Usa el argumento opcional `optimize` con

```
@code_typed optimize=true foo(x)
```

para controlar si se aplican optimizaciones adicionales, como la inlining.

Ver también: [`code_typed`](@ref), [`@code_warntype`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref), [`@code_native`](@ref).
