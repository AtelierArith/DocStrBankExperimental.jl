```
addenv(command::Cmd, env...; inherit::Bool = true)
```

Fügen Sie neue Umgebungszuordnungen in das gegebene [`Cmd`](@ref) Objekt ein und geben Sie ein neues `Cmd` Objekt zurück. Doppelte Schlüssel werden ersetzt. Wenn `command` keine Umgebungswerte enthält, die bereits festgelegt sind, erbt es die aktuelle Umgebung zum Zeitpunkt des `addenv()` Aufrufs, wenn `inherit` `true` ist. Schlüssel mit dem Wert `nothing` werden aus der Umgebung gelöscht.

Siehe auch [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref).

!!! compat "Julia 1.6"
    Diese Funktion erfordert Julia 1.6 oder höher.

