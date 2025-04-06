```
@code_native
```

Évalue les arguments de l'appel de fonction ou de macro, détermine leurs types et appelle [`code_native`](@ref) sur l'expression résultante.

Définissez n'importe quel des arguments optionnels `syntax`, `debuginfo`, `binary` ou `dump_module` en les plaçant avant l'appel de fonction, comme ceci :

```
@code_native syntax=:intel debuginfo=:default binary=true dump_module=false f(x)
```

  * Définissez la syntaxe d'assemblage en réglant `syntax` sur `:intel` (par défaut) pour la syntaxe Intel ou `:att` pour la syntaxe AT&T.
  * Spécifiez la verbosité des commentaires de code en réglant `debuginfo` sur `:source` (par défaut) ou `:none`.
  * Si `binary` est `true`, imprimez également le code machine binaire pour chaque instruction précédée d'une adresse abrégée.
  * Si `dump_module` est `false`, ne pas imprimer les métadonnées telles que rodata ou directives.

Voir aussi : [`code_native`](@ref), [`@code_warntype`](@ref), [`@code_typed`](@ref), [`@code_lowered`](@ref), [`@code_llvm`](@ref).
