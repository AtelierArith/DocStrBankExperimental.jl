```
Regex(pattern[, flags]) <: AbstractPattern
```

Un type représentant une expression régulière. Les objets `Regex` peuvent être utilisés pour faire correspondre des chaînes avec [`match`](@ref).

Les objets `Regex` peuvent être créés en utilisant le macro de chaîne [`@r_str`](@ref). Le constructeur `Regex(pattern[, flags])` est généralement utilisé si la chaîne `pattern` doit être interpolée. Voir la documentation du macro de chaîne pour des détails sur les flags.

!!! note
    Pour échapper les variables interpolées, utilisez `\Q` et `\E` (par exemple `Regex("\\Q$x\\E")`)

