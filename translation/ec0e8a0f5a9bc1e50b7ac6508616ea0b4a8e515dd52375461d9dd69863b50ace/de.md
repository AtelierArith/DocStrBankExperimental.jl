```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

Behandelt jedes nicht-standardmäßige Tastendruckereignis. Wenn `true` zurückgegeben wird, wird [`TerminalMenus.request`](@ref) beendet. Standardmäßig ist es `false`.
