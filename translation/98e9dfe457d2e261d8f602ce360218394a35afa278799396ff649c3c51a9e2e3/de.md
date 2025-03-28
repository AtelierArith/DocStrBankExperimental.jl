```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

Druckt `xs` in einer Farbe, die als Symbol oder Ganzzahl angegeben ist, optional fett.

Das Schlüsselwort `color` kann einen der Werte `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white` oder `:yellow` oder eine Ganzzahl zwischen 0 und 255 annehmen. Beachten Sie, dass nicht alle Terminals 256 Farben unterstützen.

Die Schlüsselwörter `bold=true`, `italic=true`, `underline=true`, `blink=true` sind selbsterklärend. Das Schlüsselwort `reverse=true` druckt mit vertauschten Vorder- und Hintergrundfarben, und `hidden=true` sollte im Terminal unsichtbar sein, kann aber dennoch kopiert werden. Diese Eigenschaften können in beliebiger Kombination verwendet werden.

Siehe auch [`print`](@ref), [`println`](@ref), [`show`](@ref).

!!! Hinweis     Nicht alle Terminals unterstützen kursiven Text. Einige Terminals interpretieren kursiv als umgekehrt oder blinkend.

!!! Kompatibilität "Julia 1.7"     Schlüsselwörter außer `color` und `bold` wurden in Julia 1.7 hinzugefügt.

!!! Kompatibilität "Julia 1.10"     Unterstützung für kursiven Text wurde in Julia 1.10 hinzugefügt.
