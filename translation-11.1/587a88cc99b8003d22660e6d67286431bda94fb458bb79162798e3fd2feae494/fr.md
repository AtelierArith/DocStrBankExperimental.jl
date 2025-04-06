```
code_native([io=stdout,], f, types; syntax=:intel, debuginfo=:default, binary=false, dump_module=true)
```

Imprime les instructions d'assemblage natif générées pour exécuter la méthode correspondant à la fonction générique donnée et à la signature de type dans `io`.

  * Définissez la syntaxe d'assemblage en réglant `syntax` sur `:intel` (par défaut) pour la syntaxe intel ou `:att` pour la syntaxe AT&T.
  * Spécifiez la verbosité des commentaires de code en réglant `debuginfo` sur `:source` (par défaut) ou `:none`.
  * Si `binary` est `true`, imprimez également le code machine binaire pour chaque instruction précédé d'une adresse abrégée.
  * Si `dump_module` est `false`, ne pas imprimer les métadonnées telles que rodata ou directives.
  * Si `raw` est `false`, les instructions peu intéressantes (comme le prologue de la fonction de point de sécurité) sont omises.

Voir aussi : [`@code_native`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref).
