```
code_llvm([io=stdout,], f, types; raw=false, dump_module=false, optimize=true, debuginfo=:default)
```

Imprime les bitcodes LLVM générés pour l'exécution de la méthode correspondant à la fonction générique donnée et à la signature de type dans `io`.

Si le mot-clé `optimize` n'est pas défini, le code sera affiché avant les optimisations LLVM. Toutes les métadonnées et les appels dbg.* sont supprimés du bitcode imprimé. Pour obtenir l'IR complet, définissez le mot-clé `raw` sur true. Pour afficher l'ensemble du module qui encapsule la fonction (avec les déclarations), définissez le mot-clé `dump_module` sur true. L'argument clé `debuginfo` peut être l'un de source (par défaut) ou none, pour spécifier la verbosité des commentaires de code.

Voir aussi : [`@code_llvm`](@ref), [`code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_native`](@ref).
