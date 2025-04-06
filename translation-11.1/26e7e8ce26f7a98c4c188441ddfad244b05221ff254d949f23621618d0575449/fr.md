```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

Configure le comportement d'un menu de sélection multiple via des arguments de mot-clé :

  * `checked` est la chaîne à imprimer lorsqu'une option a été sélectionnée. Les valeurs par défaut sont "[X]" ou "✓", selon `charset`.
  * `unchecked` est la chaîne à imprimer lorsqu'une option n'a pas été sélectionnée. Les valeurs par défaut sont "[ ]" ou "⬚", selon `charset`.

Tous les autres arguments de mot-clé sont décrits pour [`TerminalMenus.Config`](@ref). `checked` et `unchecked` ne sont pas imprimés automatiquement et doivent être imprimés par votre méthode `writeline`.

!!! compat "Julia 1.6"
    `MultiSelectConfig` est disponible depuis Julia 1.6. Sur les versions plus anciennes, utilisez le `CONFIG` global.

