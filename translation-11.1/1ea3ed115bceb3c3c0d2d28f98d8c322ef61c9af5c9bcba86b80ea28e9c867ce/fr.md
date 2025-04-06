```
code_warntype([io::IO], f, types; debuginfo=:default)
```

Imprime les AST abaissés et inférés par type pour les méthodes correspondant à la fonction générique donnée et à la signature de type pour `io`, qui par défaut est `stdout`. Les AST sont annotés de manière à mettre en évidence les types "non-feuilles" qui peuvent poser des problèmes de performance (s'ils sont disponibles en couleur, affichés en rouge). Cela sert d'avertissement sur une éventuelle instabilité de type.

Tous les types non-feuilles ne sont pas particulièrement problématiques pour la performance, et les caractéristiques de performance d'un type particulier sont un détail d'implémentation du compilateur. `code_warntype` aura tendance à colorer les types en rouge s'ils pourraient poser un problème de performance, donc certains types peuvent être colorés en rouge même s'ils n'impactent pas la performance. Les petites unions de types concrets ne posent généralement pas de problème, donc celles-ci sont mises en évidence en jaune.

L'argument clé `debuginfo` peut être l'un de `:source` ou `:none` (par défaut), pour spécifier la verbosité des commentaires de code.

Voir la section [`@code_warntype`](@ref man-code-warntype) dans la page des Conseils de Performance du manuel pour plus d'informations.

Voir aussi : [`@code_warntype`](@ref), [`code_typed`](@ref), [`code_lowered`](@ref), [`code_llvm`](@ref), [`code_native`](@ref).
