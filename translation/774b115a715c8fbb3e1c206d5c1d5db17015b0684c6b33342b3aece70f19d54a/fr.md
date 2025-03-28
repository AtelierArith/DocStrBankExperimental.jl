```
@code_llvm
```

Évalue les arguments de l'appel de fonction ou de macro, détermine leurs types et appelle [`code_llvm`](@ref) sur l'expression résultante. Définissez les arguments de mot-clé optionnels `raw`, `dump_module`, `debuginfo`, `optimize` en les plaçant avec leur valeur avant l'appel de fonction, comme ceci :

```
@code_llvm raw=true dump_module=true debuginfo=:default f(x)
@code_llvm optimize=false f(x)
```

`optimize` contrôle si des optimisations supplémentaires, telles que l'inlining, sont également appliquées. `raw` rend toutes les métadonnées et les appels dbg.* visibles. `debuginfo` peut être l'un de `:source` (par défaut) ou `:none`, pour spécifier la verbosité des commentaires de code. `dump_module` imprime l'ensemble du module qui encapsule la fonction.

Voir aussi : [`code_llvm`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_native`](@ref).
