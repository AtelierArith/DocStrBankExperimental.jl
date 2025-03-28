```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

Gère tout événement de pression de touche non standard. Si `true` est retourné, [`TerminalMenus.request`](@ref) sortira. Par défaut, c'est `false`.
