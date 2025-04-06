```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

Bearbeiten Sie eine Datei oder ein Verzeichnis und geben Sie optional eine Zeilennummer an, um die Datei an dieser Stelle zu bearbeiten. Kehren Sie zum `julia`-Prompt zurück, wenn Sie den Editor verlassen. Der Editor kann geändert werden, indem `JULIA_EDITOR`, `VISUAL` oder `EDITOR` als Umgebungsvariable festgelegt wird.

!!! compat "Julia 1.9"
    Das Argument `column` erfordert mindestens Julia 1.9.


Siehe auch [`InteractiveUtils.define_editor`](@ref).
