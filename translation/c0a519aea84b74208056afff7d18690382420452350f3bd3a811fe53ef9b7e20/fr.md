```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

Configure le comportement des menus de sélection via des arguments de mot-clé :

  * `scroll_wrap`, si `true`, fait en sorte que le menu se replie lorsque l'on fait défiler au-dessus de la première entrée ou en dessous de la dernière entrée
  * `ctrl_c_interrupt`, si `true`, lance une `InterruptException` si l'utilisateur appuie sur Ctrl-C pendant la sélection du menu. Si `false`, [`TerminalMenus.request`](@ref) renverra le résultat par défaut de [`TerminalMenus.selected`](@ref).
  * `charset` affecte les valeurs par défaut pour `cursor`, `up_arrow` et `down_arrow`, et peut être `:ascii` ou `:unicode`
  * `cursor` est le caractère imprimé pour indiquer l'option qui sera choisie en appuyant sur "Entrée". Les valeurs par défaut sont '>' ou '→', selon `charset`.
  * `up_arrow` est le caractère imprimé lorsque l'affichage n'inclut pas la première entrée. Les valeurs par défaut sont '^' ou '↑', selon `charset`.
  * `down_arrow` est le caractère imprimé lorsque l'affichage n'inclut pas la dernière entrée. Les valeurs par défaut sont 'v' ou '↓', selon `charset`.

Les sous-types de `ConfiguredMenu` imprimeront `cursor`, `up_arrow` et `down_arrow` automatiquement si nécessaire, votre méthode `writeline` ne doit pas les imprimer.

!!! compat "Julia 1.6"
    `Config` est disponible depuis Julia 1.6. Sur les versions plus anciennes, utilisez le `CONFIG` global.

