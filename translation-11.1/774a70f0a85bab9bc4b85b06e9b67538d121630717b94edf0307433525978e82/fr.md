```
@code_typed
```

Évalue les arguments de l'appel de fonction ou de macro, détermine leurs types et appelle [`code_typed`](@ref) sur l'expression résultante. Utilisez l'argument optionnel `optimize` avec

```
@code_typed optimize=true foo(x)
```

pour contrôler si des optimisations supplémentaires, telles que l'inlining, sont également appliquées.

Voir aussi : [`code_typed`](@ref), [`@code_warntype`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref), [`@code_native`](@ref).
