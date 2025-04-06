```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

Herhangi bir standart dışı tuş basma olayını işleyin. Eğer `true` dönerse, [`TerminalMenus.request`](@ref) çıkacaktır. Varsayılan olarak `false`'dur.
