```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

Maneja cualquier evento de pulsación de tecla no estándar. Si se devuelve `true`, [`TerminalMenus.request`](@ref) saldrá. Por defecto es `false`.
