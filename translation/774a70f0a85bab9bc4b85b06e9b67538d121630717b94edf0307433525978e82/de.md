```
@code_typed
```

Bewertet die Argumente des Funktions- oder Makroaufrufs, bestimmt deren Typen und ruft [`code_typed`](@ref) auf dem resultierenden Ausdruck auf. Verwenden Sie das optionale Argument `optimize` mit

```
@code_typed optimize=true foo(x)
```

um zu steuern, ob zusätzliche Optimierungen, wie Inlining, ebenfalls angewendet werden.

Siehe auch: [`code_typed`](@ref), [`@code_warntype`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref), [`@code_native`](@ref).
